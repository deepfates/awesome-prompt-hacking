[[ReadItLater]] [[Article]]

# [Getting tabular data from unstructured text with GPT-3: an ongoing experiment – Roberto Rocha](https://robertorocha.info/getting-tabular-data-from-unstructured-text-with-gpt-3-an-ongoing-experiment/)

[![](ReadItLater%20Inbox/assets/image-1.png)](https://robertorocha.info/wp-content/uploads/2022/10/image-1.png)

One of the most exciting applications of AI in journalism is the creation of structured data from unstructured text.

Government reports, legal documents, emails, memos… these are rich with content like names, organizations, dates, and prices. But to get them into a format that can be analyzed and counted, like a spreadsheet, usually involves days or weeks of tedious manual data entry.

Large language models like [GPT-3 from OpenAI](https://beta.openai.com/playground) have the potential to greatly speed up this awful slog. Because these models have such a deep grasp of language (GPT-3 was trained on basically the entire internet — at least all of English Wikipedia), they can understand commands and pick out the right elements from text.

## The challenge

The Canadian federal lobbyist registry has a lot of information about who is lobbying government officials, and on whose behalf. One of the most important elements of the registry is the past public offices data: lobbyists who previously worked for the government.

The data is pretty structured, showing the offices held and the time period. Here’s an example for a lobbyist [working for TikTok](https://lobbycanada.gc.ca/app/secure/ocl/lrs/do/vwRg?cno=367326&regId=921157).

[![](ReadItLater%20Inbox/assets/image.png)](https://robertorocha.info/wp-content/uploads/2022/10/image.png)

But this data has only been structured since 2008. Before that, lobbyists could enter anything into the registry. Like this:

1959- 1985 Operations, training and staff positions 1985 -1987 Base Commander, CFB Greenwood, N.S. 1987 - 1989 Commander Northern Region 1989 - 1990 Commander Maritime Air Group 1992 - 1993 Assistant Deputy Minister Personnel, NDHQ 1993 - 1995 Vice Chief of the Air Staff, NDHQ

There are thousands of entries like this. How to make them formatted neatly like more recent records?

## It’s all about the prompts

I ran a sample of 34 such job descriptions through GPT-3 with different commands, called prompts. I got different results with each prompt. None of them were perfect, but some were pretty good. Some manual fixing would still be needed.

There’s no right way to write a prompt, you just have to try different things. This is turning into a new specialization called prompt engineering. [Simon Willison](https://simonwillison.net/), a developer who builds valuable journalism tools, calls this the AI equivalent of casting spells.

Here are the results of my experiments.

You can create a [free account](https://beta.openai.com/signup) to try GPT-3 with some starting credits, but you’ll need a paid account to go further.

These are the 34 rows of data that I tried to convert to tabular data. I used the same rows in all my attempts to compare results.

1996-1997 EXECUTIVE ASSISTANT MINISTER OF TRANSPORT
Special Assistant 1991-1993 Hon. Robert Kaplan
September 1984 - February 1988 Senior Policy Analyst - various assignments related to federal procurement and trade policy Department of Supply and Services
January 2002 May 2002 Chief of Staff Office of the Minister of Public Works and Government Services Canada
OFFICES HELD WITHIN PWGSC June 1987 - November 1995 Director General, AMES (Aerospace & Marine Electronic Sector) July 1985 - May 1987 Director, Canadian Arsenals Limited Privatization Team April 1984 - June 1985 Director, Aerospace Procurement Branch July 1983 - March 1984 Procurement Director, CF18 Project Office June 1978 - Jan 1983 Director, Electronics Procurement June 1972 - May 1978 Division Chief, No 1 Division Electronics
Administrative Coordinator to the Minister of Jobs, Tourism, Skills Training and Labour
1971-79 Various junior officer positions Gagetown, NB; Lahr, Germany
1996 - 1997 - Media Relations Officer, Preston Manning, MP
Ministerial Assistant to the Minister of Transportation
Canadian Armed Forces 1959 1995
June 1988 - December 1990 MARCOM HQ Halifax Deputy Chief of Staff Readiness- National Defence
April 1996- July 1999 ADM (Materiel)
1982 -1983 -Advanced Training Biloxi, Mississippi, USA
- 2002 - LEGISLATIVE ASSISTANT - OFFICE OF LYNNE YELICH, MP
Nov. 1981 - Sept 1984, Director of Research, Progressive Conservative Caucus, House of Commons
\* June 2000-September 2001 Office of Karen Redman, M.P. Special Assistant
1991-1993 Special Assistant, Jim Peterson, M.P. (Willowdale)
Caucus Liaison, office of the Prime Minister 1985-1987
Prime Minister's Office, Research Assistant
1959- 1985 Operations, training and staff positions 1985 -1987 Base Commander, CFB Greenwood, N.S. 1987 - 1989 Commander Northern Region 1989 - 1990 Commander Maritime Air Group 1992 - 1993 Assistant Deputy Minister Personnel, NDHQ 1993 - 1995 Vice Chief of the Air Staff, NDHQ
Policy Analyst, Dept. of National Health and Welfare, 1973-74
PARLIAMENTARY SECRETARY TO MINISTER OF FINANCE
April 1995 to June 1997 Office of the Minister of International Trade Special Assistant to the Minister
Apr 1976 - Jun 1976 - trainee, Basic Helicopter School, 1 Canadian Forces Flight Training School, Rank - Lieutenant, CFB Portage La Prairie
Left government in August 1989.
August 1983 - September 1984 Director, Intergovernmental Affairs Special Recovery Capital Project Program Ministry of State for Economic and Regional Development
September 1981-September 1984 - Senior Exploration Geologist, PetroCanada (InterChange Canada program)
1982: Senior Officer, Government Org., Privy Council Office
CANADIAN ARMED FORCES 1968-2001
I served as Canada's Minister of Transport, Minister of Human Resources, and Minister of Defence.
EXECUTIVE INTERCHANGE
1980 - 1982 - Base Telecommunication Officer, CFB Montreal
Capitaine et pilote de CF-5 et de CF-104, BFC Cold Lake, 1980-1981;
1965 1971 Procurement Officer/Department of Supply & Services

### First attempt

Here was the first prompt I tried, and the resulting table.

Create a three-column table with the first date, last date, and job description for each line of text below. Treat each line as a row. If there is no date or job description, leave the column blank.

Use this format:

first date | last date | job description

And the result:

1996-1997 | | Executive Assistant Minister of Transport
1991-1993 | | Special Assistant
1984-1988 | | Senior Policy Analyst
2002 | | Chief of Staff
1987-1995 | | Director General
1985-1987 | | Director
1983-1984 | | Procurement Director
1972-1978 | | Division Chief
1971-1979 | | Various junior officer positions
1998-1999 | | Administrative Coordinator to the Minister of Jobs, Tourism, Skills Training and Labour
1996 | | Media Relations Officer
2002 | | Legislative Assistant
2000-2001 | | Special Assistant
1985-1987 | | Caucus Liaison
1973-1974 | | Policy Analyst
1995-1997 | | Parliamentary Secretary to Minister of Finance
1976-1976 | | trainee
1989 | | left government
1983-1984 | | Director
1981-1984 | | Senior Exploration Geologist
1982 | | Senior Officer
1968-2001 | | Canadian Armed Forces
1980-1982 | | Base Telecommunication Officer
1965-1971 | | Procurement Officer

Here it is, as an actual table. from now on, all results will be displayed in tables for better viewing.

| 1996-1997 |  | Executive Assistant Minister of Transport |
| --- | --- | --- |
| 1991-1993 |  | Special Assistant |
| 1984-1988 |  | Senior Policy Analyst |
| 2002 |  | Chief of Staff |
| 1987-1995 |  | Director General |
| 1985-1987 |  | Director |
| 1983-1984 |  | Procurement Director |
| 1972-1978 |  | Division Chief |
| 1971-1979 |  | Various junior officer positions |
| 1998-1999 |  | Administrative Coordinator to the Minister of Jobs, Tourism, Skills Training and Labour |
| 1996 |  | Media Relations Officer |
| 2002 |  | Legislative Assistant |
| 2000-2001 |  | Special Assistant |
| 1985-1987 |  | Caucus Liaison |
| 1973-1974 |  | Policy Analyst |
| 1995-1997 |  | Parliamentary Secretary to Minister of Finance |
| 1976-1976 |  | trainee |
| 1989 |  | left government |
| 1983-1984 |  | Director |
| 1981-1984 |  | Senior Exploration Geologist |
| 1982 |  | Senior Officer |
| 1968-2001 |  | Canadian Armed Forces |
| 1980-1982 |  | Base Telecommunication Officer |
| 1965-1971 |  | Procurement Officer |

Already, this is impressive. Given the wide variety of formats in the text, GPT-3 understood dates and job descriptions, and put them in the right order. But there are some problems:

-   The years weren’t separated into their own columns
-   Months were removed
-   Only the job titles were kept. The government departments were left out.
-   A lot of rows were skipped! There are only 24 rows, when I provided 34. It looks like it skipped anything without a date.

### Second attempt

I was advised by smarter and more experienced AI users to give GPT-3 some examples of inputs and expected outputs. So this was my next prompt.

Create a three-column table with the first date, last date, and job description for each line of text below. Treat each line as a row. Do not skip any rows.

Examples of inputs and expected outputs:

Input: 
1994-1996 POLICY ANALYST NATIONAL LIBERAL RESEARCH BUREAU
Output:
1994 | 1996 | POLICY ANALYST NATIONAL LIBERAL RESEARCH BUREAU

Input:
Sept 1984 - Sept 1985, Prime Minister's Office, Special Advisor, Research & Policy
Output:
Sept 1984 | Sept 1985 | Prime Minister's Office, Special Advisor, Research & Policy

Input:
CANADIAN INTERNATIONAL DEVELOPMENT AGENCY Office of the President, Policy Advisor July 1998 to April 2001
Output:
July 1998 | April 2001 | CANADIAN INTERNATIONAL DEVELOPMENT AGENCY Office of the President, Policy Advisor

Input:
1995-03 Legislative Assistant, Member of Parliament for Kenora-Rainy River
Output:
1995 | 2003 | Legislative Assistant, Member of Parliament for Kenora-Rainy River

Input:
Feb 1988 - 1996
Output:
Feb 1988 | 1999 |

Input:
2003  Legislative Assistant
Output:
2003 | | Legislative Assistant

And this was the result:

| 1996 | 1997 | EXECUTIVE ASSISTANT MINISTER OF TRANSPORT |
| --- | --- | --- |
| Special Assistant 1991 | 1993 | Hon. Robert Kaplan |
| September 1984 | February 1988 | Senior Policy Analyst – various assignments related to federal procurement and trade policy Department of Supply and Services |
| January 2002 | May 2002 | Chief of Staff Office of the Minister of Public Works and Government Services Canada |
| OFFICES HELD WITHIN PWGSC June 1987 | November 1995 | Director General, AMES (Aerospace & Marine Electronic Sector) July 1985 |
| Administrative Coordinator to the Minister of Jobs, Tourism, Skills Training and Labour |  |  |
| 1971 | 1979 | Various junior officer positions Gagetown, NB; Lahr, Germany |
| 1996 | 1997 | Media Relations Officer, Preston Manning, MP |
| Ministerial Assistant to the Minister of Transportation |  |  |
| Canadian Armed Forces 1959 | 1995 |  |
| June 1988 | December 1990 | MARCOM HQ Halifax Deputy Chief of Staff Readiness- National Defence |
| April 1996 | July 1999 | ADM (Materiel) |
| 1982 | 1983 | Advanced Training Biloxi, Mississippi, USA |
| \-2002 |  | LEGISLATIVE ASSISTANT – OFFICE OF LYNNE YELICH, MP |
| Nov. 1981 | Sept 1984 | Director of Research, Progressive Conservative Caucus, House of Commons |
| \* June 2000 | September 2001 | Office of Karen Redman, M.P. Special Assistant |
| 1991 | 1993 | Special Assistant, Jim Peterson, M.P. (Willowdale) |
| Caucus Liaison, office of the Prime Minister 1985 | 1987 |  |
| Prime Minister’s Office, Research Assistant |  |  |
| 1959 | 1985 | Operations, training and staff positions 1985 |
| Policy Analyst, Dept. of National Health and Welfare, 1973 | 1974 |  |
| PARLIAMENTARY SECRETARY TO MINISTER OF FINANCE |  |  |
| April 1995 | June 1997 | Office of the Minister of International Trade Special Assistant to the Minister |
| Apr 1976 | Jun 1976 | trainee, Basic Helicopter School, 1 Canadian Forces Flight Training School, Rank – Lieutenant, CFB Portage La Prairie |
| Left government in August 1989. |  |  |
| August 1983 | September 1984 | Director, Intergovernmental Affairs Special Recovery Capital Project Program Ministry of State for Economic and Regional Development |
| September 1981 | September 1984 | Senior Exploration Geologist, PetroCanada (InterChange Canada program) |
| 1982 | Senior Officer, Government Org., Privy Council Office |  |
| CANADIAN ARMED FORCES 1968 | 2001 |  |
| I served as Canada’s Minister of Transport, Minister of Human Resources, and Minister of Defence. |  |  |
| EXECUTIVE INTERCHANGE |  |  |
| 1980 | 1982 | Base Telecommunication Officer, CFB Montreal |
| Capitaine et pilote de CF-5 et de CF-104, BFC Cold Lake, 1980 | 1981; |  |
| 1965 | 1971 | Procurement Officer/Department of Supply & Services |

Already there’s an improvement. Dates are complete with months and placed into separate columns. But dates that aren’t at the start of the text weren’t placed in the first columns.

### Third attempt

I specified what to do with dates in the middle of the text:

Create a three-column table with the first date, last date, and job description for each line of text below. Treat each line as a row. Do not skip any rows. If the dates are in the middle or the end of a row, place them in the first two columns and concatenate the text that surround them on the third column. If there are more than two dates and more than one job description in each row, extract the earliest date and the latest date, and concatenate the job descriptions using a semicolon as separator.

Result:

| 1996 | 1997 | EXECUTIVE ASSISTANT MINISTER OF TRANSPORT |
| --- | --- | --- |
| 1991 | 1993 | Special Assistant, Hon. Robert Kaplan |
| September 1984 | February 1988 | Senior Policy Analyst – various assignments related to federal procurement and trade policy Department of Supply and Services |
| January 2002 | May 2002 | Chief of Staff Office of the Minister of Public Works and Government Services Canada |
| June 1987 | November 1995 | Director General, AMES (Aerospace & Marine Electronic Sector) |
| July 1985 | May 1987 | Director, Canadian Arsenals Limited Privatization Team |
| April 1984 | June 1985 | Director, Aerospace Procurement Branch |
| July 1983 | March 1984 | Procurement Director, CF18 Project Office |
| June 1978 | Jan 1983 | Director, Electronics Procurement |
| June 1972 | May 1978 | Division Chief, No 1 Division Electronics |
| 1971 | 1979 | Various junior officer positions Gagetown, NB; Lahr, Germany |
| 1996 | 1997 | Media Relations Officer, Preston Manning, MP |
| April 1996 | July 1999 | ADM (Materiel) |
| 1982 | 1983 | Advanced Training Biloxi, Mississippi, USA |
| – | 2002 | LEGISLATIVE ASSISTANT – OFFICE OF LYNNE YELICH, MP |
| Nov. 1981 | Sept 1984 | Director of Research, Progressive Conservative Caucus, House of Commons |
| \* June 2000 | September 2001 | Office of Karen Redman, M.P. Special Assistant |
| 1991 | 1993 | Special Assistant, Jim Peterson, M.P. (Willowdale) |
| Caucus Liaison, office of the Prime Minister 1985 | 1987 |  |
| August 1983 | September 1984 | Director, Intergovernmental Affairs Special Recovery Capital Project Program Ministry of State for Economic and Regional Development |
| September 1981 | September 1984 | Senior Exploration Geologist, PetroCanada (InterChange Canada program) |
| 1982 |  | Senior Officer, Government Org., Privy Council Office |
| 1968 | 2001 | CANADIAN ARMED FORCES |
| 1980 | 1982 | Base Telecommunication Officer, CFB Montreal |
| 1965 | 1971 | Procurement Officer/Department of Supply & Services |

Much better. But it went back to skipping rows! And it turned this doozy into multiple rows, which is NOT good if you want to join the extracted rows to the original data:

OFFICES HELD WITHIN PWGSC June 1987 - November 1995 Director General, AMES (Aerospace & Marine Electronic Sector) July 1985 - May 1987 Director, Canadian Arsenals Limited Privatization Team April 1984 - June 1985 Director, Aerospace Procurement Branch July 1983 - March 1984 Procurement Director, CF18 Project Office June 1978 - Jan 1983 Director, Electronics Procurement June 1972 - May 1978 Division Chief, No 1 Division Electronics

### Fourth and final attempt

I gave it two more examples:

Input:
PARLIAMENTARY SECRETARY TO MINISTER OF FINANCE
Output:
| | PARLIAMENTARY SECRETARY TO MINISTER OF FINANCE

Input:
June 1988 - September 1999 Director General, AMES (Aerospace & Marine Electronic Sector) July 1987 - May 1988 Director, Canadian Arsenals Limited Privatization Team April 1983 - June 1987 Director, Aerospace Procurement Branch July 1980 - March 1983 Procurement Director, CF18 Project Office
Output:
July 1980 |  September 1999 | Director General, AMES (Aerospace & Marine Electronic Sector);  Director, Canadian Arsenals Limited Privatization Team; Director, Aerospace Procurement Branch, Procurement Director, CF18 Project Office

Result:

| 1996 | 1997 | EXECUTIVE ASSISTANT MINISTER OF TRANSPORT |
| --- | --- | --- |
| 1991 | 1993 | Special Assistant, Hon. Robert Kaplan |
| September 1984 | February 1988 | Senior Policy Analyst – various assignments related to federal procurement and trade policy Department of Supply and Services |
| January 2002 | May 2002 | Chief of Staff Office of the Minister of Public Works and Government Services Canada |
| June 1987 | November 1995 | Director General, AMES (Aerospace & Marine Electronic Sector) |
| July 1985 | May 1987 | Director, Canadian Arsenals Limited Privatization Team |
| April 1984 | June 1985 | Director, Aerospace Procurement Branch |
| July 1983 | March 1984 | Procurement Director, CF18 Project Office |
| June 1978 | Jan 1983 | Director, Electronics Procurement |
| June 1972 | May 1978 | Division Chief, No 1 Division Electronics |
| 1971 | 1979 | Various junior officer positions Gagetown, NB; Lahr, Germany |
| 1996 | 1997 | Media Relations Officer, Preston Manning, MP |
| Ministerial Assistant to the Minister of Transportation |  |  |
| Canadian Armed Forces 1959 | 1995 |  |
| June 1988 | December 1990 | MARCOM HQ Halifax Deputy Chief of Staff Readiness- National Defence |
| April 1996 | July 1999 | ADM (Materiel) |
| 1982 | 1983 | Advanced Training Biloxi, Mississippi, USA |
| – | – | LEGISLATIVE ASSISTANT – OFFICE OF LYNNE YELICH, MP |
| Nov. 1981 | Sept 1984 | Director of Research, Progressive Conservative Caucus, House of Commons |
| \* | – | Office of Karen Redman, M.P. Special Assistant |
| 1991 | 1993 | Special Assistant, Jim Peterson, M.P. (Willowdale) |
| Caucus Liaison, office of the Prime Minister 1985 | 1987 |  |
| Prime Minister’s Office, Research Assistant |  |  |
| 1959 | 1985 | Operations, training and staff positions 1985 |
| Policy Analyst, Dept. of National Health and Welfare, 1973 | 1974 |  |
|  |  | PARLIAMENTARY SECRETARY TO MINISTER OF FINANCE |
| April 1995 | June 1997 | Office of the Minister of International Trade Special Assistant to the Minister |
| Apr 1976 | Jun 1976 | trainee, Basic Helicopter School, 1 Canadian Forces Flight Training School, Rank – Lieutenant, CFB Portage La Prairie |
|  |  | Left government in August 1989. |
| August 1983 | September 1984 | Director, Intergovernmental Affairs Special Recovery Capital Project Program Ministry of State for Economic and Regional Development |
| September 1981 | September 1984 | Senior Exploration Geologist, PetroCanada (InterChange Canada program) |
| 1982 |  | Senior Officer, Government Org., Privy Council Office |
| CANADIAN ARMED FORCES 1968 | 2001 |  |
|  |  | I served as Canada’s Minister of Transport, Minister of Human Resources, and Minister of Defence. |
| EXECUTIVE INTERCHANGE |  |  |
| 1980 | 1982 | Base Telecommunication Officer, CFB Montreal |
|  |  | Capitaine et pilote de CF-5 et de CF-104, BFC Cold Lake, 1980 |
| 1965 | 1971 | Procurement Officer/Department of Supply & Services |

At this point, I gave up. The data wasn’t perfect, but it was the best I’d be able to get with the time and money I was willing to put into it. But that’s the nature of data, there are always garbage records that need to be discarded, with hopefully a big enough sample to be usable.

## Takeaways

If you’re thinking of using AI to turn raw text into data, here are my main conclusions:

-   Be prepared to write A LOT of prompts to get the ideal output. It doesn’t cost a lot of money to test. The four attempts I showed here cost me 18 U.S. cents to process. Obviously, when you run it on larger data it will cost more. Be aware of the rates.
-   The data will probably never come out perfect. Be prepared to do plenty of manual fixing. It’s still better than doing everything from scratch.
-   Be prepared to adapt the output to the original source data. In my last attempt, it added multiple rows for one record with multiple dates. You may need to create a many-to-one relationship with the source.
-   Consider [fine-tuning GPT-3](https://beta.openai.com/docs/guides/fine-tuning) with even more examples. This is a bit more technical and requires coding.
-   **NEW:** Use the GPT-3 API, instead of the playground UI, to process one line at a time, as suggested by Arben below, in the comments.

Have you had luck using GPT-3 to get data out of text? Share your tips in the comments!