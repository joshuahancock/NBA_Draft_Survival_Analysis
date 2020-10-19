<center> <h1>NBA Draft Survival Analysis</h1> </center>
<center> <h3>Updated October 19, 2020</h3> </center>

---
#### Motivation
In preparation for the 2020 NBA Draft, we wanted to analyze when each prospect was likely to be selected. Compiling 20 mock drafts from various draft analysts, we created a survival analysis which calculated the probability of each prospect being available at each draft slot.

As an example, the following plot illustrates the probability that Anthony Edwards is available at each draft slot. Moving from right to left on the x-axis, we observe that based on the compiled mock drafts there is ~45% probability Edwards is available at pick number 2 and ~30% probability he is available at pick number 3.

<div style="text-align:center"><img src='plots/players/anthony_edwards.png' width=70%></div>

<br>

Survival analysis is typically used to calculate the probability of death occurring at a given age for subsets of the population. In this case, we've substituting being drafted for death and draft slot for age. The time between the start of the analysis and when the event of interest occurs is called survival time, which in this case is the number of draft slots that a player is still available in each mock draft.

The analysis calculates probabilities for picks 1-60. Not all players were included in each mock draft and not every mock draft ranked players 1-60 with most only ranking through the first round. Since those players were never observed we've considered them right-censored. This means that we have some information about their expected selection, in most cases they were not selected picks 1-30, but not the exact slot in which the analyst had them mocked. Due to this constraint, we've used the Kaplan-Meier estimator to calculate the survival curve of each prospect.


#### Mock Drafts

Each player's survival curve is based on information compiled from 20 mock drafts listed below. We've not included the underlying data in this repo as two mocks are behind a paywall, but have stated when each was last updated. We'll check for updates and re-run the analysis on a weekly basis in the run-up to the draft. If you see any updates we've missed or mocks we should add let us know! Thanks to all of these individuals who publish their mock drafts, especially to those who do it in tabular form.

| Name  | Affiliation  | Updated  | Mock Draft  |
|---|---|---|---|
| Babcock Hoops  | Babcock Hoops  | October 5  | [Link](https://www.babcockhoops.com/mockdraft)  |
| Bryan Kalbrosky  | Rookie Wire  | August 20  | [Link](https://therookiewire.usatoday.com/lists/2020-nba-mock-draft-all-60-picks-post-lottery/)  |
| Chris Stone  | Sporting News  | March 24  | [Link](https://www.sportingnews.com/us/nba/news/nba-mock-draft-2020-warriors-pick-timberwolves-lamelo-ball/178cr8zivu85e1qdtavgxp9cc2)  |
| Danny Cunningham  | Complex  | October 12  | [Link](https://www.complex.com/sports/nba-mock-draft-predictions-post-nba-finals/?utm_campaign=sportstw&utm_source=twitter.com&utm_medium=social)  |
| Draft Express  | ESPN  | August 20  | [Link](https://www.espn.com/nba/insider/story/_/id/29695731/nba-mock-draft-projected-picks-big-lottery-winners)  |
| Gary Parrish  | CBS Sports  | October 9  | [Link](https://www.cbssports.com/nba/draft/mock-draft/)  |
| James Ham  | NBC Sports | October 12  | [Link](https://www.nbcsports.com/bayarea/warriors/2020-nba-mock-draft-180-first-round-pick-projections-after-lakers-win-finals)  |
| Jeff Goodman  | Stadium  | August 21  | [Link](https://watchstadium.com/jeff-goodmans-2020-nba-mock-draft-3-0-lottery-order-revealed-08-20-2020/)  |
| Jeremy Woo  | Sports Illustrated  | October 14  | [Link](https://www.si.com/nba/2020/10/14/nba-mock-draft-projections-post-finals)  |
| Jonathan Wasserman  | Bleacher Report  | October 6  | [Link](https://bleacherreport.com/articles/2912058-2020-nba-mock-draft-simulating-3-trades-in-historically-unpredictable-lottery)  |
| Kevin O'Connor  | The Ringer  | October 14  | [Link](https://nbadraft.theringer.com/)  |
| Kevin Pelton  | ESPN  | June 24  | [Link](https://www.espn.com/nba/insider/story/_/id/29335461/2020-nba-draft-projections-ranking-top-30-prospects)  |
| Krysten Peek  | Yahoo Sports  | October 15  | [Link](https://sports.yahoo.com/2020-nba-mock-draft-50-la-melo-moves-to-no-1-132728170.html)  |
| Kyle Boone  | CBS Sports  | October 15  | [Link](https://www.cbssports.com/nba/draft/mock-draft/)  |
| NBAdraftnet | NBAdraftnet | September 16 | [Link](https://www.nbadraft.net/nba-mock-drafts/) |
| NetScouts  | NetScouts  | October 5  | [Link](https://netscoutsbasketball.com/scouting/2020-nba-mock-draft/)  |
| Ricky O'Donnell  | SB Nation  | August 20  | [Link](https://www.sbnation.com/nba/2020/8/20/21374098/nba-mock-draft-2020-lottery-order-timberwolves-warriors-bulls)  |
| Sam Veceine  | The Athletic  | October 13  | [Link](https://theathletic.com/2128239/2020/10/13/lamelo-ball-over-james-wiseman-at-no-1-in-2020-nba-mock-draft-version-8-0/)  |
| Scott Gleeson  | USA Today  | August 20  | [Link](https://www.usatoday.com/story/sports/nba/draft/2020/08/20/nba-mock-draft-post-lottery-timberwolves-top-pick/3402893001/)  |
| Tankathon  | Tankathon  | ~ August  | [Link](http://www.tankathon.com/mock_draft)  |

#### Consensus Top-3 Picks

Based on the average draft slot across all mock drafts, Anthony Edwards (1.8), LaMelo Ball (2.2), and James Wiseman (3.5) are the consensus top three picks. Their respective survival curves are plotted below. At this point in time only Ball and Edwards are expected to be selected in the top two picks. Ball and Wiseman have low probabilities of lasting to picks 9 and 17, respectively, as a few mocks have them going quite low.

<div style="text-align:center"><img src='plots/top_3.png' width=90%></div>

#### Consensus Top-10 Picks

In similar fashion, here are the survival curves of the consensus top-10 picks. Six of the top ten have a non-zero chance of falling out of the lottery according to the mock drafts. One thing we have our eye on is any future movement in Devin Vassell's curve after the suspected [change to his shooting form](https://twitter.com/Joe_Casey1/status/1316803378182262784?s=20) that have [some analysts questining their opinion of him](https://twitter.com/johnhollinger/status/1316794770220556288?s=20).

<div style="text-align:center"><img src='plots/top_10.png' width=90%></div>

#### Case Studies

At this point the mock drafts have Anthony Edwards as the most likely first overall pick. There's ~45% probability he is available at the number two pick and ~30% chance he is available at the third pick. Based on the mocks there is no chance he falls to the 5th pick.

<div style="text-align:center"><img src='plots/players/anthony_edwards.png' width=90%></div>

<br>

Xavier Tillman provides a good example of a player likely to go in the middle of the draft. Based on the mock drafts, he is unlikely to be selected prior to the 23rd slot. After then his probability of being available decreases at a steady rate. He is likely to be gone by pick 52.

<div style="text-align:center"><img src='plots/players/xavier_tillman.png' width=90%></div>

<br>

Kenyon Martin Jr. is a player on the fringe of being drafted. The mock drafts have him unlikely to be selected prior to pick number 56. In total, there is ~60% probability he goes undrafted.

<div style="text-align:center"><img src='plots/players/kenyon_martin_jr.png' width=90%></div>

<br>

Hopefully this analysis provides additional information for teams on when targeted players might be available during the draft. As a final example, if you're a hypothetical team targeting a point guard outside of the lottery you can compare survival curves to better predict when a player will be available. In this case, if you value Maledon over Flynn and Terry you'll need to be more aggressive in moving up to get him as he's likely to be gone before the other two.

<br>

<div style="text-align:center"><img src='plots/pg_example.png' width=90%></div>

#### Dashboard
To interactively filter to a specific player, visit our [dashboard](https://chrisfeller.shinyapps.io/nba_draft_survival_analysis_app/?_ga=2.67843986.2071066075.1603058532-829731406.1603058532).

<div style="text-align:center"><img src='plots/dashboard_example.png' width=90%></div>

#### References
1. [Lifelines Package Documentation](https://lifelines.readthedocs.io/en/latest/index.html)
2. Emily Zabor - *[Survival Analysis in R](https://www.emilyzabor.com/tutorials/survival_analysis_in_r_tutorial.html#part_1:_introduction_to_survival_analysis)*
3. Savvas Tjortjoglou - *[Surviving the NFL](http://savvastjortjoglou.com/nfl-survival-analysis-kaplan-meier.html)*
