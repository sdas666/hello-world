# hello-world
SELECT tA.FieldName As [Field Name],
       COALESCE(tO_A.[desc], tO_B.[desc], tO_C.Name, tA.OldVAlue) AS [Old Value],
       COALESCE(tN_A.[desc], tN_B.[desc], tN_C.Name, tA.NewValue) AS [New Value],
       U.UserName AS [User Name],
       CONVERT(varchar, tA.ChangeDate) AS [Change Date] 
  FROM D tA
       JOIN 
       [DRTS].[dbo].[User] U 
         ON tA.UserID = U.UserID
       LEFT JOIN 
       A tO_A 
         on tA.FieldName = 'AID' 
        AND tA.oldValue = CONVERT(VARCHAR, tO_A.ID)
       LEFT JOIN 
       A tN_A 
