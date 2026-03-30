CREATE VIEW [dbo].[sv_tweets_fev2026]
AS
WITH RankedPosts AS (
    SELECT 
        *,
        ROW_NUMBER() OVER (PARTITION BY post_id ORDER BY post_id) AS rn
    FROM fev2026
)
SELECT
       [Query_Str]
      ,[Post_URL]
      ,[Author_Name] AS Author_Name
      ,[Author_Web_Page_URL] AS [Author_Web_Page_URL]
      ,[Author_Handle] AS [Author_Handle]
      ,[Verified_Status]
      ,[UTC_Time]
      ,[Ads]
      ,TRIM((
        SELECT STRING_AGG(value, ' ')
        FROM STRING_SPLIT(tweet_content, ' ')
        WHERE value NOT LIKE 'http%'  
          AND value NOT LIKE 'www.%' 
        )) AS Tweet_Content
      ,[Post_ID]
      ,dbo.MaskString80([Tweet_URL]) AS [Tweet_URL]
      ,[Reply_Count]
      ,[Repost_Count]
      ,[Like_Count]
      ,[View_Count]
      ,[Bookmark_Count]
      ,[Tweet_Image_URL]
      ,[Replying_to]
      ,[Reply_to_Whom]
      ,[Reply_to_Whom_URL]
      ,[Reply_to_Whom_Username]
      ,[Reply_to_Whom_Handle]
      ,[Language]
      ,[Type]
FROM RankedPosts
WHERE rn = 1 and (Tweet_Content LIKE '%china%' OR Tweet_Content LIKE '%chinês%' OR Tweet_Content LIKE '%chines%' OR Tweet_Content LIKE '%pequim%' OR Tweet_Content LIKE '%dinastia%'
 OR Tweet_Content LIKE '%jinping%')