# MisFit

Stray Dogs Attack Prevention System. Residents report dog trouble by pin code, and the app turns the answers into a red, yellow or green zone.

## What it does

- Register and log in as a Public user or a Department user.
- Fill in a survey: pin code, district, how often dogs are a problem, how many dogs you saw this week, and whether you were bitten.
- Look up a pin code on the Heat Map page to get its zone.

## How it works

Each survey answer is stored in a MySQL `survey` table with the user, pin code and a timestamp. For a pin code, the app adds up the "dogs seen this week" answers, divides by the number of responses and maps the average to a zone: above 2.75 is Red, above 1.75 is Yellow, below that is Green (`checkHeatmap.jsp`, `HeatmapProcess.jsp`).

The heat map is a zone label per pin code. There is no map drawing.

## Stack

- Java, JSP, servlet listener (Eclipse dynamic web project)
- MySQL via JDBC (`mysql-connector-j` is bundled in `WEB-INF/lib`)
- HTML, CSS

## Run it locally

Roughly: import the project into Eclipse (or any IDE with a servlet container), deploy it on Tomcat and open `index.jsp`.

You also need a MySQL server on `localhost:3306` with a database named `misfit` and `login` and `survey` tables. The database credentials are hardcoded in the JSPs and `MyListener.java`, and no schema script for these two tables exists in the repo. Expect to set them up by hand.

## Notes

Finalist at the Dr. Pradeep P. Thevannoor Hackathon (2022). Built in 24 hours with [HariCodesHere](https://github.com/HariCodesHere).
The base is a quiz-site template, so the quiz pages (take quiz, ask question, contact) are leftovers and do nothing for the dog-safety idea. A navigation bar on the survey page links to an SOS page that was never built.
