# Election_Analysis

## Overview of Election Audit
The objective is to assist Tom to analyze the results of the congressional election. We have a database with three columns (Ballot ID, County, and Candidate) and a total of 369,712 rows. The database contains a personal ID for each voter, the county name, and the candidate's name.

For this analysis we are interested in knowing who the candidates are, the total number of votes and the percentage of each candidate, as well as identify the winning candidate.

Additionally, The election commission has requested some additional data to complete the audit:

1) The voter turnout for each county
2) The percentage of votes from each county out of the total count
3) The county with the highest turnout


## Election-Audit Results
Using a bulleted list, address the following election outcomes. Use images or examples of your code as support where necessary.

- **How many votes were cast in this congressional election?**

we need to make a for to count the total number of votes. We have a total of **369,711 votes.**

Code:
        
        for row in reader:
                total_votes = total_votes + 1

![](https://github.com/Jponce25/Election_Analysis/blob/1abab17e1a8a015fe71b7d77a430fa9cda1658b6/Resources/Imagen1.png)

- **Provide a breakdown of the number of votes and the percentage of total votes for each county in the precinct.**

We have three counties, Denver is the county with the highest number of voters with **306,055** *(82.8%)* followed by Jefferson with **38,855** *(10.5%)* and Arapahoe with **24,801** *(6.7%)*.

Code:

        for county_name in county_votes:
                county = county_votes.get(county_name)
                county_porcentage = float(county)/ float(total_votes) * 100

                county_results = (
                    f"{county_name}: {county_porcentage:.1f}% ({county:,})\n")
                print (county_results, end="")

![](https://github.com/Jponce25/Election_Analysis/blob/1abab17e1a8a015fe71b7d77a430fa9cda1658b6/Resources/Imagen2.png)

- **Which county had the largest number of votes?**

According to the data the largest county turnout is **Denver with 306,055 voters.**

Code:

        if (county > largest_count):
            largest_count = county
            largest_turnout = county_name

![](https://github.com/Jponce25/Election_Analysis/blob/1abab17e1a8a015fe71b7d77a430fa9cda1658b6/Resources/Imagen3.png)

- **Provide a breakdown of the number of votes and the percentage of the total votes each candidate received.**

We have 3 candidates, Diana DeGette is the candidate with the highest number of votes with **272,892** *(73.8%)*, followed by Charles Casper with **85,213** *(23.0%)* and Raymon Anthony with **11,606** *(3.1%)*.

Code:

        for candidate_name in candidate_votes:
                Retrieve vote count and percentage
                votes = candidate_votes.get(candidate_name)
                vote_percentage = float(votes) / float(total_votes) * 100
                candidate_results = (
                    f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")
               
                print(candidate_results)

![](https://github.com/Jponce25/Election_Analysis/blob/1abab17e1a8a015fe71b7d77a430fa9cda1658b6/Resources/Imagen4.png)

- **Which candidate won the election, what was their vote count, and what was their percentage of the total votes?**

According to the data **Diana DeGette is the absolute winner of the election**, with a total of *73.8%* (272,892) of the votes.

Code:

        if (votes > winning_count) and (vote_percentage > winning_percentage):
            winning_count = votes
            winning_candidate = candidate_name
            winning_percentage = vote_percentage

![](https://github.com/Jponce25/Election_Analysis/blob/1abab17e1a8a015fe71b7d77a430fa9cda1658b6/Resources/Imagen5.png)

## Election-Audit Summary

This script can be used for future elections, in fact changing the original base (.csv) and the name of the writing file (.txt) we can use it even for other states elections.

Code: 

        # Add a variable to load a file from a path.
        file_to_load = os.path.join("Resources", "election_results.csv")
        # Add a variable to save the file to a path.
        file_to_save = os.path.join("analysis", "election_analysis.txt")

We could even modify the code to obtain the results of the elections and get the winner, winner vote count and porcentage in each of the counties to really know the performance of the candidates. Regardless of the number of candidates, voters or counties. The code is designed to run and print the results, that is, it is intended to be used in other elections or in larger elections.