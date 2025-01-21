# 2024.06 - 2024.09
**Description**: development of Digital ConOps web service. The service has to aggregate all the data related to concept development stage such as stakeholders list, their need and problems, Requirements elicited, potential solutions for the task with staged timeline and description of each stage.
**Conclusion**: The web-servise is finished according to specified functionality requirements. It had no further use because it brings no value to the potential customer comparing it with traditional documents. 

The code for web-service is presented at [github](https://github.com/pleaseaddhyphens/Digital-ConOps), the architecture is presented at [[Architecture canvas.canvas|Architecture canvas]]. The ER-diagram representing digital model is presented here [[Digital_conops_infomodel_v8.drawio.png]]

The Gannt chart with work planned is presented at the [[Gantt_Immersion.xlsx]] with all the work performed during that period.

Immersion  poser is presented in the following file highlighting the formal work done.
[[Immersion Poster_Tikhonenko_v2.pptx]]

At the las summer SELT meeting the retrospective session was conducted describing what was done and the potential development of selt further ("Нужно начать уже работать")
[[V_retrospective_and plans_2024_08_28.pptx]]
#
### Library:
1. International Standard that specifies requirement engineering process [[iso-iec-ieee-29148-2011.pdf]]
2. IT project management book. The document provides comprehensive guidelines how to mange IT project. The templates for stakeholders and requirements is provided aswell.  [[IT-PM-Selikhovkin.pdf]] 
3. SELT high level concept of operation slides is presented at [[SELT_Product vision_v.3_Clemant.pptx]]
4. Guide lines for value chain building and analysis [[Value_Chain_Research_Methodology.pdf]] 

# 2024.09- 2024.12
**Description**: development of system engineering light weight tool (SELT) as a refinement of open-source software such as Gaphor. It was python development. At first we clone gaphor repository and start to change upstream code. It was wrong idea, it's hard to assemble cross-platform application, special developers keys is required to establish proper installation procedure (to pass windows defender or other virus protection soft). 
Instead the external plugin was developed that seamlessly could be installed using official Gaphor application as the basis.
**Conclusion**: the developed plugin was tested in system engineering course 2024. It shows some gaps in usability of the software. Industrial feedback shows mild support. Mostly engineers seeks of software with PLM / PDM functionalities. The two shows desire to pilot the concept - None of them start use it by the end of the year. Overall, seems customer doesn't have the pain that is solved by our software - **no Value**. 

Work plan that was expected to complete is presented at [google docs](https://docs.google.com/spreadsheets/d/1SCFrJ7eW92B_vYdn75Qmp3z0rNpmQNDrDprTCpgR-JE/edit?gid=1115838130#gid=1115838130)

The interviews were conducted with industry representatives presented at files: [[Interview Dmitry Zaitsev]] and [[Interview Yan Stolyarov]]. In summary, they stated unforecasted technical and cost risks.

The interview spontaneously conducted with Alexander revealed that there is lack of communication between contractor and customer [[Interview with Alexander]]

The visual prototype were developed showing how concept map could look like. The draw.io file:[[V_прототип_SELT_сортировака_фров.drawio]], png file preview: [[V_прототип_SELT_сортировака_фров-Система в общем.png]]

The metamodel describing what are the elements and how they interconnected is provided preview: [[V_selt_basik brick_v2.drawio.pdf]], source:[[V_selt_basik brick_v2.drawio]]. This was the initial metamodel, before gaphor plugin start developing.

On thought come to mind that for the [[complex system involving multiple engineering teams it is feasible to have standardly unified visual representation]]

During product development there were good contact with "Бюро 1440" that is developing satellite constellation similar with "Starlink". They wanted to implement Teamcenter PLM and tune their business processes. Overall, they were eager to find the technical coach that would resolve conflicts arising from process changes.
Different departments had different needs and key driver for those needs. The idea was to use SELT to map needs and conflicts to resolve them. details here [[Предложение_для_1440.docx]]

Meanwhile the system engineering course for 1440 employees (BSTU mostly) was conducted. They use selt for the modeling purposes. their final works presented here [[conops_bauman_2.pptx]],  [[conops_bauman_3.pptx]], [[conops_bauman_1.pptx]]. The main observation is that students tend to overload diagram with the elements making it unreadable for the presentation. As well, simple tabular representation is perceived better than visual diagram.

SELT was tested at system engineering course 2024. Using pip as plugin installer, it take 6-7 people who had troubles with installation - so it is easier to run to production web-app instead of desktop in terms of testing. Here is the installation guide [[Guide for SELT modeling tool installation 1]] here is the modeling guide [[Modeling guide 1]]. Here is the students homework assignments completed: [[SELT_homework.zip]]
Interesting not so many people ask for the help with modeling or app installation.  

There were the case where could implement SELT and strategic session. It had to consider desing-to-cost retrospective analysis for "ПД-8" aircraft engine. Here is the file with requirements for that integration [[требования_к_внедрению.docx]]

The Feature of Ideal PDM that is elicited from potential users is presented here [[Идеальна PDM]] 

### Software Development

The code itslef is presented at [github](https://github.com/pleaseaddhyphens/selt-model-plugin)
Initially it was decided to create branch from gaphor repository. But it was wrong, we were unable to properly assemble installer (it requires windows authorization as developer). 

The problems and solutions that arise during development process is presented here [[Проблемы и решения gaphor 1]]. Most of the problems were cause of we tried to create application from source code. It was for 1.5 month and just before selt introduction in two days the plugin was created giving the ability to install and use the application.  

The selt architecture presented at and described. [[How to develop the plugin for gaphor]]:
