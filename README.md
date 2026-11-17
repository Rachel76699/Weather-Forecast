# Jerusalem Weather MCP

A local MCP server that provides 7-day weather forecasts for Jerusalem using the Open-Meteo API. Built with Python and designed to integrate with VS Code Copilot.

שרת MCP מקומי שמספק כלי לתחזית מזג האוויר בירושלים לשבעת הימים הקרובים. הנתונים מתקבלים מ־[Open-Meteo](https://open-meteo.com/) ללא מפתח API. הטמפרטורות במעלות צלזיוס, מהירות הרוח בקמ״ש, והשעות לפי אזור הזמן של ירושלים.

## דרישות

- Python 3.10 ומעלה
- חיבור לאינטרנט בזמן בקשת התחזית

## התקנה והרצה

פתחו טרמינל PowerShell בתיקיית הפרויקט, והריצו את הפקודות הבאות:

```powershell
& "$env:LOCALAPPDATA\Programs\Python\Python313\python.exe" -m venv .venv
& ".\.venv\Scripts\python.exe" -m pip install -e .
```

אם Python מותקן במיקום אחר, החליפו את הנתיב לפייתון המותקן אצלכם. לאחר ההתקנה, אפשר להריץ ידנית:

```powershell
& ".\.venv\Scripts\python.exe" -m jerusalem_weather_mcp
```

השרת משתמש בתעבורת `stdio` ומיועד להפעלה על ידי לקוח MCP, למשל VS Code. כשהוא מופעל ידנית הוא ימתין בשקט לבקשות MCP.

## חיבור ל־VS Code

קובץ `.vscode/mcp.json` כבר מצורף לפרויקט ומשתמש בסביבת `.venv` שנוצרה בפקודות ההתקנה למעלה. פתחו את תיקיית `weather_forecast` ב־VS Code. לחצו `Ctrl+Shift+P`, חפשו `MCP: List Servers`, בחרו `jerusalem-weather` ואז `Start Server`. בכלי הצ'אט אפשר לבקש להפעיל את `jerusalem_weekly_forecast`.

חשוב לפתוח ב־VS Code את תיקיית הפרויקט עצמה, כדי שנתיב `${workspaceFolder}` יפנה למקום הנכון.

## הכלי

`jerusalem_weekly_forecast` מחזיר אובייקט עם פרטי מיקום, אזור זמן, מקור הנתונים ורשימה של שבע תחזיות יומיות. כל יום כולל תיאור בעברית, קוד מזג אוויר, טמפרטורות מינימום ומקסימום, סיכוי מרבי למשקעים, מהירות רוח מרבית וזריחה/שקיעה.

## בדיקות

```powershell
& ".\.venv\Scripts\python.exe" -m unittest discover -s tests
```
