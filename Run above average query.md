# Query for Run above average
```sql
WITH cte1 AS (
    SELECT 
        striker,
        COUNT(ball_by_ball.ball_id) AS balls_faced,
        SUM(batsman_scored.runs_scored) AS runs_made
    FROM 
        ball_by_ball
        LEFT JOIN batsman_scored
        ON ball_by_ball.match_id = batsman_scored.match_id
        AND ball_by_ball.innings_no = batsman_scored.innings_no
        AND ball_by_ball.over_id = batsman_scored.over_id
        AND ball_by_ball.ball_id = batsman_scored.ball_id
    GROUP BY striker
),

cte2 AS (
    SELECT
        striker,
        balls_faced,
        runs_made,
        COALESCE(COUNT(wicket_taken.ball_id), 0) AS outs
    FROM 
        cte1 
        LEFT JOIN wicket_taken
        ON cte1.striker = wicket_taken.player_out
    GROUP BY striker, balls_faced, runs_made
)

SELECT
    player.player_name,
    runs_made - SUM(runs_made) OVER()::DECIMAL / SUM(balls_faced) OVER() * balls_faced
    + runs_made::DECIMAL / outs * balls_faced * 
    (SUM(outs) OVER()::DECIMAL / SUM(balls_faced) OVER() - outs::DECIMAL / balls_faced) AS raa,
    RANK() OVER (ORDER BY 
        runs_made - SUM(runs_made) OVER()::DECIMAL / SUM(balls_faced) OVER() * balls_faced
        + runs_made::DECIMAL / outs * balls_faced * 
        (SUM(outs) OVER()::DECIMAL / SUM(balls_faced) OVER() - outs::DECIMAL / balls_faced) DESC
    )
FROM 
    cte2 
    JOIN player
    ON cte2.striker = player.player_id
WHERE 
    balls_faced > 0 AND outs > 0
ORDER BY 
    raa DESC;

```
