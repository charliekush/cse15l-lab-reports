#Part 1 - Bugs

## A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)

```
    @Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
    
```
## An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)
```
    @Test 
	public void testReverseInPlace3() {
        int[] input1 = {  };
        ArrayExamples.reverseInPlace(input1);
        assertArrayEquals(new int[]{  }, input1);
	}
```

## The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)
![Symptom](https://github.com/charliekush/cse15l-lab-reports/blob/91e38080abbb83c3d2e140f042180a487432f6b9/Screenshot%202023-11-19%20at%2011.07.20%20PM.png)

## The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)
Before:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
        arr[i] = arr[arr.length - i - 1];
    }
}
```

After:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length / 2; i += 1) {
        int tmp = arr[i];
        arr[i] = arr[arr.length - i - 1];
        arr[arr.length - i - 1] = tmp;
    }
}
```

## An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)

The code works for getting the last  half of the elements to the front however, there is no swapping that takes place. It simply copies the elements from the back to the front but overwrites the front elements without doing anything with them. The reimplementation runs half as many times and swaps both elements in the same iteration of the loop.  

# Part 2 - Researching Commands
Command: grep 

## Command Line Option 1: grep -E
### Example 1:
Input and output:
```
$ grep -E "American 77|United 93" ./technical/911report/* 
    ./technical/911report/chapter-1.txt:    Washington Dulles: American 77. Hundreds of miles southwest of Boston, at Dulles International Airport in the Virginia suburbs of Washington, D.C., five more men were preparing to take their early morning flight. At 7:15, a pair of them, Khalid al Mihdhar and Majed Moqed, checked in at the American Airlines ticket counter for Flight 77, bound for Los Angeles. Within the next 20 minutes, they would be followed by Hani Hanjour and two brothers, Nawaf al Hazmi and Salem al Hazmi.
    ./technical/911report/chapter-1.txt:    Newark: United 93. Between 7:03 and 7:39, Saeed al Ghamdi, Ahmed al Nami, Ahmad al Haznawi, and Ziad Jarrah checked in at the United Airlines ticket counter for Flight 93, going to Los Angeles. Two checked bags; two did not. Haznawi was selected by CAPPS. His checked bag was screened for explosives and then loaded on the plane.
    ./technical/911report/chapter-1.txt:    The Hijacking of American 77 American Airlines Flight 77 was scheduled to depart from Washington Dulles for Los Angeles at 8:10. The aircraft was a Boeing 757 piloted by Captain Charles F. Burlingame and First Officer David Charlebois. There were four flight attendants. On September 11, the flight carried 58 passengers.
    ./technical/911report/chapter-1.txt:    American 77 pushed back from its gate at 8:09 and took off at 8:20. At 8:46, the flight reached its assigned cruising altitude of 35,000 feet. Cabin service would have begun. At 8:51, American 77 transmitted its last routine radio communication. The hijacking began between 8:51 and 8:54. As on American 11 and United 175, the hijackers used knives (reported by one passenger) and moved all the passengers (and possibly crew) to the rear of the aircraft (reported by one flight attendant and one passenger). Unlike the earlier flights, the Flight 77 hijackers were reported by a passenger to have box cutters. Finally, a passenger reported that an announcement had been made by the "pilot" that the plane had been hijacked. Neither of the firsthand accounts mentioned any stabbings or the threat or use of either a bomb or Mace, though both witnesses began the flight in the first-class cabin.
    ./technical/911report/chapter-1.txt:    At 9:00, American Airlines Executive Vice President Gerard Arpey learned that communications had been lost with American 77. This was now the second American aircraft in trouble. He ordered all American Airlines flights in the Northeast that had not taken off to remain on the ground. Shortly before 9:10, suspecting that American 77 had been hijacked, American headquarters concluded that the second aircraft to hit the World Trade Center might have been Flight 77. After learning that United Airlines was missing a plane, American Airlines headquarters extended the ground stop nationwide.
    ./technical/911report/chapter-1.txt:    At 9:29, the autopilot on American 77 was disengaged; the aircraft was at 7,000 feet and approximately 38 miles west of the Pentagon.
    ./technical/911report/chapter-1.txt:    At 9:34, Ronald Reagan Washington National Airport advised the Secret Service of an unknown aircraft heading in the direction of the White House. American 77 was then 5 miles west-southwest of the Pentagon and began a 330-degree turn. At the end of the turn, it was descending through 2,200 feet, pointed toward the Pentagon and downtown Washington. The hijacker pilot then advanced the throttles to maximum power and dove toward the Pentagon.
    ./technical/911report/chapter-1.txt:    The Battle for United 93 At 8:42, United Airlines Flight 93 took off from Newark (New Jersey) Liberty International Airport bound for San Francisco. The aircraft was piloted by Captain Jason Dahl and First Officer Leroy Homer, and there were five flight attendants. Thirty-seven passengers, including the hijackers, boarded the plane. Scheduled to depart the gate at 8:00, the Boeing 757's takeoff was delayed because of the airport's typically heavy morning traffic.
    ./technical/911report/chapter-1.txt:    The hijackers had planned to take flights scheduled to depart at 7:45 (American 11), 8:00 (United 175 and United 93), and 8:10 (American 77). Three of the flights had actually taken off within 10 to 15 minutes of their planned departure times. United 93 would ordinarily have taken off about 15 minutes after pulling away from the gate. When it left the ground at 8:42, the flight was running more than 25 minutes late.
    ./technical/911report/chapter-1.txt:    As United 93 left Newark, the flight's crew members were unaware of the hijacking of American 11. Around 9:00, the FAA, American, and United were facing the staggering realization of apparent multiple hijackings. At 9:03, they would see another aircraft strike the World Trade Center. Crisis managers at the FAA and the airlines did not yet act to warn other aircraft.
    ./technical/911report/chapter-1.txt:    United 175 was hijacked between 8:42 and 8:46, and awareness of that hijacking began to spread after 8:51. American 77 was hijacked between 8:51 and 8:54. By 9:00, FAA and airline officials began to comprehend that attackers were going after multiple aircraft. American Airlines' nationwide ground stop between 9:05 and 9:10 was followed by a United Airlines ground stop. FAA controllers at Boston Center, which had tracked the first two hijackings, requested at 9:07 that Herndon Command Center "get messages to airborne aircraft to increase security for the cockpit." There is no evidence that Herndon took such action. Boston Center immediately began speculating about other aircraft that might be in danger, leading them to worry about a transcontinental flight-Delta 1989-that in fact was not hijacked. At 9:19, the FAA's New England regional office called Herndon and asked that Cleveland Center advise Delta 1989 to use extra cockpit security.
    ./technical/911report/chapter-1.txt:    The airlines bore responsibility, too. They were facing an escalating number of conflicting and, for the most part, erroneous reports about other flights, as well as a continuing lack of vital information from the FAA about the hijacked flights. We found no evidence, however, that American Airlines sent any cockpit warnings to its aircraft on 9/11. United's first decisive action to notify its airborne aircraft to take defensive action did not come until 9:19, when a United flight dispatcher, Ed Ballinger, took the initiative to begin transmitting warnings to his 16 transcontinental flights: "Beware any cockpit intrusion- Two a/c [aircraft] hit World Trade Center." One of the flights that received the warning was United 93. Because Ballinger was still responsible for his other flights as well as Flight 175, his warning message was not transmitted to Flight 93 until 9:23.
    ./technical/911report/chapter-1.txt:    By all accounts, the first 46 minutes of Flight 93's cross-country trip proceeded routinely. Radio communications from the plane were normal. Heading, speed, and altitude ran according to plan. At 9:24, Ballinger's warning to United 93 was received in the cockpit. Within two minutes, at 9:26, the pilot, Jason Dahl, responded with a note of puzzlement: "Ed, confirm latest mssg plz-Jason."
    ./technical/911report/chapter-1.txt:    The hijackers attacked at 9:28. While traveling 35,000 feet above eastern Ohio, United 93 suddenly dropped 700 feet. Eleven seconds into the descent, the FAA's air traffic control center in Cleveland received the first of two radio transmissions from the aircraft. During the first broadcast, the captain or first officer could be heard declaring "Mayday" amid the sounds of a physical struggle in the cockpit. The second radio transmission, 35 seconds later, indicated that the fight was continuing. The captain or first officer could be heard shouting:" Hey get out of here-get out of here-get out of here."
    ./technical/911report/chapter-1.txt:    On the morning of 9/11, there were only 37 passengers on United 93-33 in addition to the 4 hijackers. This was below the norm for Tuesday mornings during the summer of 2001. But there is no evidence that the hijackers manipulated passenger levels or purchased additional seats to facilitate their operation.
    ./technical/911report/chapter-1.txt:    Because several passengers on United 93 described three hijackers on the plane, not four, some have wondered whether one of the hijackers had been able to use the cockpit jump seat from the outset of the flight. FAA rules allow use of this seat by documented and approved individuals, usually air carrier or FAA personnel. We have found no evidence indicating that one of the hijackers, or anyone else, sat there on this flight. All the hijackers had assigned seats in first class, and they seem to have used them. We believe it is more likely that Jarrah, the crucial pilot-trained member of their team, remained seated and inconspicuous until after the cockpit was seized; and once inside, he would not have been visible to the passengers.
    ./technical/911report/chapter-1.txt:    One of the callers from United 93 also reported that he thought the hijackers might possess a gun. But none of the other callers reported the presence of a firearm. One recipient of a call from the aircraft recounted specifically asking her caller whether the hijackers had guns. The passenger replied that he did not see one. No evidence of firearms or of their identifiable remains was found at the aircraft's crash site, and the cockpit voice recorder gives no indication of a gun being fired or mentioned at any time. We believe that if the hijackers had possessed a gun, they would have used it in the flight's last minutes as the passengers fought back.
    ./technical/911report/chapter-1.txt:    Jarrah's objective was to crash his airliner into symbols of the American Republic, the Capitol or the White House. He was defeated by the alerted, unarmed passengers of United 93.
    ./technical/911report/chapter-1.txt:    American Airlines Flight 77 FAA Awareness. American 77 began deviating from its flight plan at 8:54, with a slight turn toward the south. Two minutes later, it disappeared completely from radar at Indianapolis Center, which was controlling the flight.
    ./technical/911report/chapter-1.txt:    The controller tracking American 77 told us he noticed the aircraft turning to the southwest, and then saw the data disappear. The controller looked for primary radar returns. He searched along the plane's projected flight path and the airspace to the southwest where it had started to turn. No primary targets appeared. He tried the radios, first calling the aircraft directly, then the airline. Again there was nothing. At this point, the Indianapolis controller had no knowledge of the situation in New York. He did not know that other aircraft had been hijacked. He believed American 77 had experienced serious electrical or mechanical failure, or both, and was gone.
    ./technical/911report/chapter-1.txt:    Shortly after 9:00, Indianapolis Center started notifying other agencies that American 77 was missing and had possibly crashed. At 9:08, Indianapolis Center asked Air Force Search and Rescue at Langley Air Force Base to look for a downed aircraft. The center also contacted the West Virginia State Police and asked whether any reports of a downed aircraft had been received. At 9:09, it reported the loss of contact to the FAA regional center, which passed this information to FAA headquarters at 9:24.
    ./technical/911report/chapter-1.txt:    By 9:20, Indianapolis Center learned that there were other hijacked aircraft, and began to doubt its initial assumption that American 77 had crashed. A discussion of this concern between the manager at Indianapolis and the Command Center in Herndon prompted it to notify some FAA field facilities that American 77 was lost. By 9:21, the Command Center, some FAA field facilities, and American Airlines had started to search for American 77. They feared it had been hijacked. At 9:25, the Command Center advised FAA headquarters of the situation.
    ./technical/911report/chapter-1.txt:    The failure to find a primary radar return for American 77 led us to investigate this issue further. Radar reconstructions performed after 9/11 reveal that FAA radar equipment tracked the flight from the moment its transponder was turned off at 8:56. But for 8 minutes and 13 seconds, between 8:56 and 9:05, this primary radar information on American 77 was not displayed to controllers at Indianapolis Center.
    ./technical/911report/chapter-1.txt:    The reasons are technical, arising from the way the software processed radar information, as well as from poor primary radar coverage where American 77 was flying.
    ./technical/911report/chapter-1.txt:    According to the radar reconstruction, American 77 reemerged as a primary target on Indianapolis Center radar scopes at 9:05, east of its last known position. The target remained in Indianapolis Center's airspace for another six minutes, then crossed into the western portion of Washington Center's airspace at 9:10. As Indianapolis Center continued searching for the aircraft, two managers and the controller responsible for American 77 looked to the west and southwest along the flight's projected path, not east-where the aircraft was now heading. Managers did not instruct other controllers at Indianapolis Center to turn on their primary radar coverage to join in the search for American 77.
    ./technical/911report/chapter-1.txt:    In sum, Indianapolis Center never saw Flight 77 turn around. By the time it reappeared in primary radar coverage, controllers had either stopped looking for the aircraft because they thought it had crashed or were looking toward the west. Although the Command Center learned Flight 77 was missing, neither it nor FAA headquarters issued an all points bulletin to surrounding centers to search for primary radar targets. American 77 traveled undetected for 36 minutes on a course heading due east for Washington, D.C.
    ./technical/911report/chapter-1.txt:    By 9:25, FAA's Herndon Command Center and FAA headquarters knew two aircraft had crashed into the World Trade Center. They knew American 77 was lost. At least some FAA officials in Boston Center and the New England Region knew that a hijacker on board American 11 had said "we have some planes." Concerns over the safety of other aircraft began to mount. A manager at the Herndon Command Center asked FAA headquarters if they wanted to order a "nationwide ground stop." While this was being discussed by executives at FAA headquarters, the Command Center ordered one at 9:25.
    ./technical/911report/chapter-1.txt:    The Command Center kept looking for American 77. At 9:21, it advised the Dulles terminal control facility, and Dulles urged its controllers to look for primary targets. At 9:32, they found one. Several of the Dulles controllers "observed a primary radar target tracking eastbound at a high rate of speed" and notified Reagan National Airport. FAA personnel at both Reagan National and Dulles airports notified the Secret Service. The aircraft's identity or type was unknown.
    ./technical/911report/chapter-1.txt:Military Notification and Response. NORAD heard nothing about the search for American 77. Instead, the NEADS air defenders heard renewed reports about a plane that no longer existed: American 11.
    ./technical/911report/chapter-1.txt:    The mention of a "third aircraft" was not a reference to American 77. There was confusion at that moment in the FAA. Two planes had struck the World Trade Center, and Boston Center had heard from FAA headquarters in Washington that American 11 was still airborne. We have been unable to identify the source of this mistaken FAA information.
    ./technical/911report/chapter-1.txt:    At the suggestion of the Boston Center's military liaison, NEADS contacted the FAA's Washington Center to ask about American 11. In the course of the conversation, a Washington Center manager informed NEADS:"We're looking- we also lost American 77." The time was 9:34. This was the first notice to the military that American 77 was missing, and it had come by chance. If NEADS had not placed that call, the NEADS air defenders would have received no information whatsoever that the flight was even missing, although the FAA had been searching for it. No one at FAA headquarters ever asked for military assistance with American 77.
    ./technical/911report/chapter-1.txt:    After the 9:36 call to NEADS about the unidentified aircraft a few miles from the White House, the Langley fighters were ordered to Washington, D.C. Controllers at NEADS located an unknown primary radar track, but "it kind of faded" over Washington. The time was 9:38. The Pentagon had been struck by American 77 at 9:37:46. The Langley fighters were about 150 miles away.
    ./technical/911report/chapter-1.txt:    But another aircraft was heading toward Washington, an aircraft about which NORAD had heard nothing: United 93.
    ./technical/911report/chapter-1.txt:    United Airlines Flight 93 FAA Awareness. At 9:27, after having been in the air for 45 minutes, United 93 acknowledged a transmission from the Cleveland Center controller. This was the last normal contact the FAA had with the flight.
    ./technical/911report/chapter-1.txt:    The controller responded, seconds later: "Somebody call Cleveland?"This was followed by a second radio transmission, with sounds of screaming. The Cleveland Center controllers began to try to identify the possible source of the transmissions, and noticed that United 93 had descended some 700 feet. The controller attempted again to raise United 93 several times, with no response. At 9:30, the controller began to poll the other flights on his frequency to determine if they had heard the screaming; several said they had.
    ./technical/911report/chapter-1.txt:    FAA headquarters had by this time established an open line of communication with the Command Center at Herndon and instructed it to poll all its centers about suspect aircraft. The Command Center executed the request and, a minute later, Cleveland Center reported that "United 93 may have a bomb on board." At 9:34, the Command Center relayed the information concerning United 93 to FAA headquarters. At approximately 9:36, Cleveland advised the Command Center that it was still tracking United 93 and specifically inquired whether someone had requested the military to launch fighter aircraft to intercept the aircraft. Cleveland even told the Command Center it was prepared to contact a nearby military base to make the request. The Command Center told Cleveland that FAA personnel well above them in the chain of command had to make the decision to seek military assistance and were working on the issue.
    ./technical/911report/chapter-1.txt:    Between 9:34 and 9:38, the Cleveland controller observed United 93 climbing to 40,700 feet and immediately moved several aircraft out its way. The controller continued to try to contact United 93, and asked whether the pilot could confirm that he had been hijacked.
    ./technical/911report/chapter-1.txt:    Then, at 9:39, a fourth radio transmission was heard from United 93: Ziad Jarrah: Uh, this is the captain. Would like you all to remain seated. There is a bomb on board and are going back to the airport, and to have our demands [unintelligible]. Please remain quiet.
    ./technical/911report/chapter-1.txt:    The controller responded: "United 93, understand you have a bomb on board. Go ahead." The flight did not respond.
    ./technical/911report/chapter-1.txt:    From 9:34 to 10:08, a Command Center facility manager provided frequent updates to Acting Deputy Administrator Monte Belger and other executives at FAA headquarters as United 93 headed toward Washington, D.C. At 9:41, Cleveland Center lost United 93's transponder signal. The controller located it on primary radar, matched its position with visual sightings from other aircraft, and tracked the flight as it turned east, then south.
    ./technical/911report/chapter-1.txt:    At 9:46 the Command Center updated FAA headquarters that United 93 was now "twenty-nine minutes out of Washington, D.C." At 9:49, 13 minutes after Cleveland Center had asked about getting military help, the Command Center suggested that someone at headquarters should decide whether to request military assistance: FAA Headquarters: They're pulling Jeff away to go talk about United 93.
    ./technical/911report/chapter-1.txt:    At 9:53, FAA headquarters informed the Command Center that the deputy director for air traffic services was talking to Monte Belger about scrambling aircraft. Then the Command Center informed headquarters that controllers had lost track of United 93 over the Pittsburgh area. Within seconds, the Command Center received a visual report from another aircraft, and informed headquarters that the aircraft was 20 miles northwest of Johnstown. United 93 was spotted by another aircraft, and, at 10:01, the Command Center advised FAA headquarters that one of the aircraft had seen United 93 "waving his wings." The aircraft had witnessed the hijackers' efforts to defeat the passengers' counterattack.
    ./technical/911report/chapter-1.txt:    United 93 crashed in Pennsylvania at 10:03:11, 125 miles from Washington, D.C. The precise crash time has been the subject of some dispute. The 10:03:11 impact time is supported by previous National Transportation Safety Board analysis and by evidence from the Commission staff 's analysis of radar, the flight data recorder, the cockpit voice recorder, infrared satellite data, and air traffic control transmissions.
    ./technical/911report/chapter-1.txt:    Five minutes later, the Command Center forwarded this update to headquarters: Command Center: O.K. Uh, there is now on that United 93.
    ./technical/911report/chapter-1.txt:    The aircraft that spotted the "black smoke" was the same unarmed Air National Guard cargo plane that had seen American 77 crash into the Pentagon 27 minutes earlier. It had resumed its flight to Minnesota and saw the smoke from the crash of United 93, less than two minutes after the plane went down. At 10:17, the Command Center advised headquarters of its conclusion that United 93 had indeed crashed.
    ./technical/911report/chapter-1.txt:    Despite the discussions about military assistance, no one from FAA headquarters requested military assistance regarding United 93. Nor did any manager at FAA headquarters pass any of the information it had about United 93 to the military.
    ./technical/911report/chapter-1.txt:Military Notification and Response. NEADS first received a call about United 93 from the military liaison at Cleveland Center at 10:07. Unaware that the aircraft had already crashed, Cleveland passed to NEADS the aircraft's last known latitude and longitude. NEADS was never able to locate United 93 on radar because it was already in the ground.
    ./technical/911report/chapter-1.txt:    At the same time, the NEADS mission crew commander was dealing with the arrival of the Langley fighters over Washington, D.C., sorting out what their orders were with respect to potential targets. Shortly after 10:10, and having no knowledge either that United 93 had been heading toward Washington or that it had crashed, he explicitly instructed the Langley fighters: "negative- negative clearance to shoot" aircraft over the nation's capital.
    ./technical/911report/chapter-1.txt:    The news of a reported bomb on board United 93 spread quickly at NEADS. The air defenders searched for United 93's primary radar return and tried to locate other fighters to scramble. NEADS called Washington Center to report: NEADS: I also want to give you a heads-up, Washington.
    ./technical/911report/chapter-1.txt:    The time of notification of the crash of United 93 was 10:15. The NEADS air defenders never located the flight or followed it on their radar scopes. The flight had already crashed by the time they learned it was hijacked.
    ./technical/911report/chapter-1.txt:    In public testimony before this Commission in May 2003, NORAD officials stated that at 9:16, NEADS received hijack notification of United 93 from the FAA. This statement was incorrect. There was no hijack to report at 9:16. United 93 was proceeding normally at that time.
    ./technical/911report/chapter-1.txt:    In this same public testimony, NORAD officials stated that at 9:24, NEADS received notification of the hijacking of American 77. This statement was also incorrect. The notice NEADS received at 9:24 was that American 11 had not hit the World Trade Center and was heading for Washington, D.C.
    ./technical/911report/chapter-1.txt:    In their testimony and in other public accounts, NORAD officials also stated that the Langley fighters were scrambled to respond to the notifications about American 77,178 United 93, or both. These statements were incorrect as well. The fighters were scrambled because of the report that American 11 was heading south, as is clear not just from taped conversations at NEADS but also from taped conversations at FAA centers; contemporaneous logs compiled at NEADS, Continental Region headquarters, and NORAD; and other records. Yet this response to a phantom aircraft was not recounted in a single public timeline or statement issued by the FAA or Department of Defense. The inaccurate accounts created the impression that the Langley scramble was a logical response to an actual hijacked aircraft.
    ./technical/911report/chapter-1.txt:    In fact, not only was the scramble prompted by the mistaken information about American 11, but NEADS never received notice that American 77 was hijacked. It was notified at 9:34 that American 77 was lost. Then, minutes later, NEADS was told that an unknown plane was 6 miles southwest of the White House. Only then did the already scrambled airplanes start moving directly toward Washington, D.C.
    ./technical/911report/chapter-1.txt:    Thus the military did not have 14 minutes to respond to American 77, as testimony to the Commission in May 2003 suggested. It had at most one or two minutes to react to the unidentified plane approaching Washington, and the fighters were in the wrong place to be able to help. They had been responding to a report about an aircraft that did not exist.
    ./technical/911report/chapter-1.txt:    Nor did the military have 47 minutes to respond to United 93, as would be implied by the account that it received notice of the flight's hijacking at 9:16. By the time the military learned about the flight, it had crashed. We now turn to the role of national leadership in the events that morning.
    ./technical/911report/chapter-1.txt:    At the White House, the video teleconference was conducted from the Situation Room by Richard Clarke, a special assistant to the president long involved in counterterrorism. Logs indicate that it began at 9:25 and included the CIA; the FBI; the departments of State, Justice, and Defense; the FAA; and the White House shelter. The FAA and CIA joined at 9:40. The first topic addressed in the White House video teleconference-at about 9:40-was the physical security of the President, the White House, and federal agencies. Immediately thereafter it was reported that a plane had hit the Pentagon. We found no evidence that video teleconference participants had any prior information that American 77 had been hijacked and was heading directly toward Washington. Indeed, it is not clear to us that the video teleconference was fully under way before 9:37, when the Pentagon was struck.
    ./technical/911report/chapter-1.txt:    By 10:03, when United 93 crashed in Pennsylvania, there had been no mention of its hijacking and the FAA had not yet been added to the teleconference.
    ./technical/911report/chapter-1.txt:    American 77 began turning south, away from the White House, at 9:34. It continued heading south for roughly a minute, before turning west and beginning to circle back. This news prompted the Secret Service to order the immediate evacuation of the Vice President just before 9:36. Agents propelled him out of his chair and told him he had to get to the bunker. The Vice President entered the underground tunnel leading to the shelter at 9:37.
    ./technical/911report/chapter-1.txt:    United 93 and the Shootdown Order On the morning of 9/11, the President and Vice President stayed in contact not by an open line of communication but through a series of calls. The President told us he was frustrated with the poor communications that morning. He could not reach key officials, including Secretary Rumsfeld, for a period of time. The line to the White House shelter conference room-and the Vice President- kept cutting off.
    ./technical/911report/chapter-1.txt:    At 10:02, the communicators in the shelter began receiving reports from the Secret Service of an inbound aircraft-presumably hijacked-heading toward Washington. That aircraft was United 93. The Secret Service was getting this information directly from the FAA. The FAA may have been tracking the progress of United 93 on a display that showed its projected path to Washington, not its actual radar return. Thus, the Secret Service was relying on projections and was not aware the plane was already down in Pennsylvania.
    ./technical/911report/chapter-1.txt:    Transmission of the Authorization from the White House to the Pilots The NMCC learned of United 93's hijacking at about 10:03. At this time the FAA had no contact with the military at the level of national command. The NMCC learned about United 93 from the White House. It, in turn, was informed by the Secret Service's contacts with the FAA.
    ./technical/911report/chapter-1.txt:    NORAD officials have maintained consistently that had the passengers not caused United 93 to crash, the military would have prevented it from reaching Washington, D.C. That conclusion is based on a version of events that we now know is incorrect. The Langley fighters were not scrambled in response to United 93; NORAD did not have 47 minutes to intercept the flight; NORAD did not even know the plane was hijacked until after it had crashed. It is appropriate, therefore, to reconsider whether United 93 would have been intercepted.
    ./technical/911report/chapter-1.txt:    Had it not crashed in Pennsylvania at 10:03, we estimate that United 93 could not have reached Washington any earlier than 10:13, and probably would have arrived before 10:23. There was only one set of fighters circling Washington during that time frame-the Langley F-16s. They were armed and under NORAD's control. After NEADS learned of the hijacking at 10:07, NORAD would have had from 6 to 16 minutes to locate the flight, receive authorization to shoot it down, and communicate the order to the pilots, who (in the same span) would have had to authenticate the order, intercept the flight, and execute the order.
    ./technical/911report/chapter-1.txt:    At that point in time, the Langley pilots did not know the threat they were facing, did not know where United 93 was located, and did not have shootdown authorization.
    ./technical/911report/chapter-1.txt:    Second, NEADS did not have accurate information on the location of United 93. Presumably FAA would have provided such information, but we do not know how long that would have taken, nor how long it would have taken NEADS to locate the target.
    ./technical/911report/chapter-1.txt:    NORAD officials have maintained that they would have intercepted and shot down United 93. We are not so sure. We are sure that the nation owes a debt to the passengers of United 93. Their actions saved the lives of countless others, and may have saved either the Capitol or the White House from destruction.
    ./technical/911report/chapter-13.2.txt:                the left and right aisles. On American 77 and United 93, Boeing 757 single-aisle
    ./technical/911report/chapter-13.2.txt:                8:47; on American 77, the signal was turned off at 8:56; and on United 93, the
    ./technical/911report/chapter-13.2.txt:            57. The records available for the phone calls from American 77 do not allow for a
    ./technical/911report/chapter-13.2.txt:                records, copies of boarding passes for United 93, Sept. 11,2001. One passenger
    ./technical/911report/chapter-13.2.txt:            76. In accordance with FAA regulations, United 93's cockpit voice recorder recorded
    ./technical/911report/chapter-13.2.txt:            85. FBI reports of investigation, interviews of recipients of calls from United 93.
    ./technical/911report/chapter-13.2.txt:                American 77 and have found no evidence that FAA headquarters issued a directive to
    ./technical/911report/chapter-13.2.txt:                materials also indicates that no one within FAA located American 77 until the
    ./technical/911report/chapter-13.2.txt:                American 77 was traveling through Washington Center's airspace. The Washington
    ./technical/911report/chapter-13.2.txt:            158. The United 93 timeline in FAA report, "Summary of Air Traffic Hijack Events
    ./technical/911report/chapter-13.2.txt:            159. The United 93 timeline in FAA report, "Summary of Air Traffic Hijack Events
    ./technical/911report/chapter-13.2.txt:                For discussions about the status of United 93, see ibid., pp. 24-27.
    ./technical/911report/chapter-13.2.txt:                September 11, 2001, whose authors conclude that the impact time of United 93 was
    ./technical/911report/chapter-13.2.txt:                These data sets constrain United 93's impact time to within 1 second, are airplane-
    ./technical/911report/chapter-13.2.txt:                37 seconds after the impact time of United 93 as established by NTSB and Commission
    ./technical/911report/chapter-13.2.txt:                log records the tail number not of American 77 but of American 11:"American Airlines
    ./technical/911report/chapter-13.2.txt:            209. American 77's route has been determined through Commission analysis of FAA and
```
Why it is useful:
I am able to search for two of the flights of 9/11 at the same time, using the regex "OR" Operator, allowing me to complete two search at once.
### Example 2:
Input and output:
```
$grep -E "[0-9]{4}" ./technical/911report/chapter-11.txt > tmp
        surprise attacks before-Pearl Harbor is one well-known case, the 1950 Chinese attack
        1990s. Americans celebrated the end of the Cold War with a mixture of relief and
        President George H.W. Bush dealt with the first of these in 1990 and 1991 when he
        Yousef, who organized the 1993 bombing of the World Trade Center, and Mir Amal
        Kansi, who in 1993 killed two CIA employees as they waited to go to work in Langley,
        depredations in the Balkans between 1995 and 1999, for example, was orders of
    As best we can determine, neither in 2000 nor in the first eight months of 2001 did
        topic in the 2000 presidential campaign. Congress and the media called little
    While we now know that al Qaeda was formed in 1988, at the end of the Soviet
        organization, at least in documents we have seen, until 1999. A National
        Intelligence Estimate distributed in July 1995 predicted future terrorist attacks
        such as sports arenas, and civil aviation generally. It warned that the 1993 World
    This 1995 estimate described the greatest danger as "transient groupings of
    In 1996-1997, the intelligence community received new information making clear that
        Ladin's organization in the 1992 attack on a Yemeni hotel quartering U.S. military
        personnel, the 1993 shootdown of U.S. Army Black Hawk helicopters in Somalia, and
        quite possibly the 1995 Riyadh bombing of the American training mission to the Saudi
        National Guard. The 1997 update of the 1995 estimate did not discuss the new
        intelligence. It did state that the terrorist danger depicted in 1995 would persist.
        1997 update was the last national estimate on the terrorism danger completed before
    From 1998 to 2001, a number of very good analytical papers were distributed on
        December 1999, al Qaeda's operational style, and the evolving goals of the Islamist
        to Attack US Aircraft [with antiaircraft missiles]" (June 1998),"Strains Surface
        Between Taliban and Bin Ladin" (January 1999), "Terrorist Threat to US Interests in
        Caucasus" (June 1999), "Bin Ladin to Exploit Looser Security During
        Holidays"(December 1999),"Bin Ladin Evading Sanctions" (March 2000),"Bin Ladin's
        Interest in Biological, Radiological Weapons" (February 2001), "Taliban Holding Firm
        on Bin Ladin for Now" (March 2001),"Terrorist Groups Said Cooperating on US Hostage
        Plot" (May 2001), and "Bin Ladin Determined to Strike in the US" (August 2001).
    Despite such reports and a 1999 paper on Bin Ladin's command structure for al Qaeda,
    In late 2000, DCI GeorgeTenet recognized the deficiency of strategic analysis against
        briefed him in March 2001 on "creating a strategic assessment capability." The CTC
        established a new strategic assessments branch during July 2001. The decision to add
        September 10, 2001.
        York Times article in April 1999 sought to debunk claims that Bin Ladin was a
            Attacks." The head of analysis at the CTC until 1999
        none was produced on terrorism between 1997 and 9/11.
    By 2001 the government still needed a decision at the highest level as to whether al
        to Condoleezza Rice on January 25, 2001. In his blistering protest about
        was coming, especially after peace talks stalemated at the end of November 1941.
        experts. In 1996, as a result of the TWA Flight 800 crash, President Clinton created
        onto planes. In late 1998, reports came in of a possible al Qaeda plan to hijack a
        1998, originated from a source who had walked into an American consulate in East
        Algerian group hijacked an airliner in 1994, most likely intending to blow it up
    In 1994, a private airplane had crashed onto the south lawn of the White House. In
        early 1995, Abdul Hakim Murad-Ramzi Yousef 's accomplice in the Manila airlines
    Clarke had been concerned about the danger posed by aircraft since at least the 1996
        to the Washington region. In 1998, Clarke chaired an exercise designed to highlight
    In late 1999, a great deal of discussion took place in the media about the crash off
        controls, and flown the aircraft into the sea. After the 1999-2000 millennium
        possibility was imaginable, and imagined. In early August 1999, the FAA's Civil
    Since the Pearl Harbor attack of 1941, the intelligence community has devoted
        conducted for DCI Robert Gates in 1992 that proposed several recommendations, among
        warning system was not looking for information such as the July 2001 FBI report of
        the August 2001 arrest of Zacarias Moussaoui because of his suspicious behavior in a
        the context of protecting the Atlanta Olympics of 1996, the White House complex, and
        the 2001 G-8 summit in Genoa.
        threatened, overwhelmed, or destroyed. Early in 2001, DCI Tenet and Deputy Director
        U.S. government received in 1996-1997, after the embassy bombings of August 1998,
        after the discoveries of the Jordanian and Ressam plots in late 1999, and after the
        attack on the USS Cole in October 2000.
        the embassy bombings of August 1998. We described those decisions in chapter 4. It
        impeachment. In addition, in 1998-99 President Clinton was preparing the government
        mid-1997, one CIA officer wrote to his supervisor: "All we're doing is holding the
        Afghanistan's U.S. interests. The warning had been given in 1998, again in late
        1999, once more in the fall of 2000, and again in the summer of 2001. Delivering it
        for the Cole attack came in during November 2000, National Security Advisor Samuel
        achieved little success beyond the collection of intelligence. After the August 1998
        had a different view. Shelton felt that the August 1998 attacks had proved a waste
        apparent than in the military establishment. After the August 1998 missile strike,
        2000, as part of a millennium after-action review. President Clinton and his
    Consider, for example, the case of Mihdhar, Hazmi, and their January 2000 trip to
        Kuala Lumpur, detailed in chapter 6. In late 1999, the National Security Agency
        unnoticed, in Los Angeles on January 15. In early March 2000, Bangkok reported that
    On December 4, 1998, DCI Tenet issued a directive to several CIA officials and his
        resources. Congress attempted to strengthen the DCI's authority in 1996 by creating
        with terrorism-the last weeks of December 1999 preceding the millennium.
    In the period between December 1999 and early January 2000, information about
    In the summer of 2001, DCI Tenet, the Counterterrorist Center, and the
        terrorist activity, and headquarters was not shaking them up. Between May 2001 and

```
Why it is useful:

## Command Line Option 2: grep -R
### Example 1:
Input and output:
```
$ grep -R " liver " ./technical/government/*
    ./technical/government/Alcohol_Problems/Session2-PDF.txt:count, liver enzymes, gamma-glutamyltransferase (GGT),
    ./technical/government/Alcohol_Problems/Session3-PDF.txt:medical conditions such as liver disease or pancreatitis.
    ./technical/government/Media/Wingates_winds.txt:abnormal liver function, among other illnesses.
```
Why it is useful:
I am able to search recursively in all files, including those nested in sub directories, of the ./technical/government/ directory for the term " liver "
### Example 2:
Input and output:
```
$ grep -R "H.R. 22" ./technical/government/* > ./tmp
    ./technical/government/Post_Rate_Comm/Mitchell_spyros-first-class.txt:For building "H.R. 22" Model, the Postal Service has assumed
```
Why it is useful:
Like the last command, I am able to search recursively in all files, including those nested in sub directories, of the ./technical/government/ directory for the term "H.R. 22". THis usage is interesting because it shows it was only found in one file.

## Command Line Option 3: grep -c
### Example 1:
Input and output:
```
$ grep -c "a" ./technical/plos/* 
./technical/plos/journal.pbio.0020001.txt:196
./technical/plos/journal.pbio.0020010.txt:72
./technical/plos/journal.pbio.0020012.txt:191
./technical/plos/journal.pbio.0020013.txt:129
./technical/plos/journal.pbio.0020019.txt:140
./technical/plos/journal.pbio.0020028.txt:176
./technical/plos/journal.pbio.0020035.txt:160
./technical/plos/journal.pbio.0020040.txt:87
./technical/plos/journal.pbio.0020042.txt:107
./technical/plos/journal.pbio.0020043.txt:215
./technical/plos/journal.pbio.0020046.txt:208
./technical/plos/journal.pbio.0020047.txt:60
./technical/plos/journal.pbio.0020052.txt:161
./technical/plos/journal.pbio.0020053.txt:239
./technical/plos/journal.pbio.0020054.txt:218
./technical/plos/journal.pbio.0020063.txt:78
./technical/plos/journal.pbio.0020064.txt:185
./technical/plos/journal.pbio.0020067.txt:118
./technical/plos/journal.pbio.0020068.txt:188
./technical/plos/journal.pbio.0020071.txt:72
./technical/plos/journal.pbio.0020073.txt:102
./technical/plos/journal.pbio.0020100.txt:88
./technical/plos/journal.pbio.0020101.txt:144
./technical/plos/journal.pbio.0020105.txt:88
./technical/plos/journal.pbio.0020112.txt:84
./technical/plos/journal.pbio.0020113.txt:229
./technical/plos/journal.pbio.0020116.txt:145
./technical/plos/journal.pbio.0020121.txt:189
./technical/plos/journal.pbio.0020125.txt:174
./technical/plos/journal.pbio.0020127.txt:147
./technical/plos/journal.pbio.0020133.txt:163
./technical/plos/journal.pbio.0020140.txt:136
./technical/plos/journal.pbio.0020145.txt:201
./technical/plos/journal.pbio.0020146.txt:202
./technical/plos/journal.pbio.0020147.txt:82
./technical/plos/journal.pbio.0020148.txt:203
./technical/plos/journal.pbio.0020150.txt:176
./technical/plos/journal.pbio.0020156.txt:107
./technical/plos/journal.pbio.0020161.txt:222
./technical/plos/journal.pbio.0020164.txt:191
./technical/plos/journal.pbio.0020169.txt:158
./technical/plos/journal.pbio.0020172.txt:115
./technical/plos/journal.pbio.0020183.txt:155
./technical/plos/journal.pbio.0020187.txt:140
./technical/plos/journal.pbio.0020190.txt:161
./technical/plos/journal.pbio.0020206.txt:212
./technical/plos/journal.pbio.0020213.txt:249
./technical/plos/journal.pbio.0020214.txt:183
./technical/plos/journal.pbio.0020215.txt:105
./technical/plos/journal.pbio.0020216.txt:124
./technical/plos/journal.pbio.0020223.txt:113
./technical/plos/journal.pbio.0020224.txt:107
./technical/plos/journal.pbio.0020228.txt:137
./technical/plos/journal.pbio.0020232.txt:181
./technical/plos/journal.pbio.0020241.txt:164
./technical/plos/journal.pbio.0020262.txt:83
./technical/plos/journal.pbio.0020263.txt:83
./technical/plos/journal.pbio.0020267.txt:222
./technical/plos/journal.pbio.0020272.txt:89
./technical/plos/journal.pbio.0020276.txt:143
./technical/plos/journal.pbio.0020297.txt:103
./technical/plos/journal.pbio.0020302.txt:167
./technical/plos/journal.pbio.0020306.txt:171
./technical/plos/journal.pbio.0020307.txt:124
./technical/plos/journal.pbio.0020310.txt:153
./technical/plos/journal.pbio.0020311.txt:148
./technical/plos/journal.pbio.0020337.txt:129
./technical/plos/journal.pbio.0020346.txt:94
./technical/plos/journal.pbio.0020347.txt:242
./technical/plos/journal.pbio.0020348.txt:173
./technical/plos/journal.pbio.0020350.txt:207
./technical/plos/journal.pbio.0020353.txt:67
./technical/plos/journal.pbio.0020354.txt:170
./technical/plos/journal.pbio.0020394.txt:189
./technical/plos/journal.pbio.0020400.txt:188
./technical/plos/journal.pbio.0020401.txt:152
./technical/plos/journal.pbio.0020404.txt:179
./technical/plos/journal.pbio.0020406.txt:244
./technical/plos/journal.pbio.0020419.txt:169
./technical/plos/journal.pbio.0020420.txt:157
./technical/plos/journal.pbio.0020430.txt:75
./technical/plos/journal.pbio.0020431.txt:118
./technical/plos/journal.pbio.0020439.txt:285
./technical/plos/journal.pbio.0020440.txt:222
./technical/plos/journal.pbio.0030021.txt:161
./technical/plos/journal.pbio.0030024.txt:142
./technical/plos/journal.pbio.0030032.txt:139
./technical/plos/journal.pbio.0030050.txt:187
./technical/plos/journal.pbio.0030051.txt:109
./technical/plos/journal.pbio.0030056.txt:157
./technical/plos/journal.pbio.0030062.txt:191
./technical/plos/journal.pbio.0030065.txt:159
./technical/plos/journal.pbio.0030076.txt:133
./technical/plos/journal.pbio.0030094.txt:153
./technical/plos/journal.pbio.0030097.txt:131
./technical/plos/journal.pbio.0030102.txt:156
./technical/plos/journal.pbio.0030105.txt:73
./technical/plos/journal.pbio.0030127.txt:193
./technical/plos/journal.pbio.0030129.txt:72
./technical/plos/journal.pbio.0030131.txt:107
./technical/plos/journal.pbio.0030136.txt:115
./technical/plos/journal.pbio.0030137.txt:216
./technical/plos/pmed.0010008.txt:285
./technical/plos/pmed.0010010.txt:135
./technical/plos/pmed.0010013.txt:123
./technical/plos/pmed.0010021.txt:139
./technical/plos/pmed.0010022.txt:68
./technical/plos/pmed.0010023.txt:39
./technical/plos/pmed.0010024.txt:39
./technical/plos/pmed.0010025.txt:31
./technical/plos/pmed.0010026.txt:68
./technical/plos/pmed.0010028.txt:422
./technical/plos/pmed.0010029.txt:32
./technical/plos/pmed.0010030.txt:35
./technical/plos/pmed.0010034.txt:88
./technical/plos/pmed.0010036.txt:385
./technical/plos/pmed.0010039.txt:158
./technical/plos/pmed.0010041.txt:84
./technical/plos/pmed.0010042.txt:111
./technical/plos/pmed.0010045.txt:265
./technical/plos/pmed.0010046.txt:71
./technical/plos/pmed.0010047.txt:46
./technical/plos/pmed.0010048.txt:49
./technical/plos/pmed.0010049.txt:44
./technical/plos/pmed.0010050.txt:38
./technical/plos/pmed.0010051.txt:93
./technical/plos/pmed.0010052.txt:177
./technical/plos/pmed.0010056.txt:165
./technical/plos/pmed.0010058.txt:172
./technical/plos/pmed.0010060.txt:130
./technical/plos/pmed.0010061.txt:85
./technical/plos/pmed.0010062.txt:307
./technical/plos/pmed.0010064.txt:328
./technical/plos/pmed.0010066.txt:270
./technical/plos/pmed.0010067.txt:29
./technical/plos/pmed.0010068.txt:28
./technical/plos/pmed.0010069.txt:43
./technical/plos/pmed.0010070.txt:43
./technical/plos/pmed.0010071.txt:58
./technical/plos/pmed.0020002.txt:120
./technical/plos/pmed.0020005.txt:106
./technical/plos/pmed.0020007.txt:119
./technical/plos/pmed.0020009.txt:187
./technical/plos/pmed.0020015.txt:261
./technical/plos/pmed.0020016.txt:288
./technical/plos/pmed.0020017.txt:157
./technical/plos/pmed.0020018.txt:425
./technical/plos/pmed.0020019.txt:34
./technical/plos/pmed.0020020.txt:40
./technical/plos/pmed.0020021.txt:31
./technical/plos/pmed.0020022.txt:32
./technical/plos/pmed.0020023.txt:38
./technical/plos/pmed.0020024.txt:33
./technical/plos/pmed.0020027.txt:26
./technical/plos/pmed.0020028.txt:20
./technical/plos/pmed.0020033.txt:97
./technical/plos/pmed.0020034.txt:215
./technical/plos/pmed.0020035.txt:64
./technical/plos/pmed.0020036.txt:69
./technical/plos/pmed.0020039.txt:149
./technical/plos/pmed.0020040.txt:187
./technical/plos/pmed.0020045.txt:376
./technical/plos/pmed.0020047.txt:43
./technical/plos/pmed.0020048.txt:14
./technical/plos/pmed.0020050.txt:309
./technical/plos/pmed.0020055.txt:67
./technical/plos/pmed.0020059.txt:402
./technical/plos/pmed.0020060.txt:138
./technical/plos/pmed.0020061.txt:228
./technical/plos/pmed.0020062.txt:136
./technical/plos/pmed.0020065.txt:41
./technical/plos/pmed.0020067.txt:154
./technical/plos/pmed.0020068.txt:175
./technical/plos/pmed.0020071.txt:117
./technical/plos/pmed.0020073.txt:482
./technical/plos/pmed.0020074.txt:32
./technical/plos/pmed.0020075.txt:107
./technical/plos/pmed.0020082.txt:16
./technical/plos/pmed.0020085.txt:27
./technical/plos/pmed.0020086.txt:23
./technical/plos/pmed.0020088.txt:72
./technical/plos/pmed.0020090.txt:36
./technical/plos/pmed.0020091.txt:39
./technical/plos/pmed.0020094.txt:35
./technical/plos/pmed.0020098.txt:90
./technical/plos/pmed.0020099.txt:97
./technical/plos/pmed.0020102.txt:135
./technical/plos/pmed.0020103.txt:432
./technical/plos/pmed.0020104.txt:74
./technical/plos/pmed.0020113.txt:42
./technical/plos/pmed.0020114.txt:41
./technical/plos/pmed.0020115.txt:39
./technical/plos/pmed.0020116.txt:36
./technical/plos/pmed.0020117.txt:37
./technical/plos/pmed.0020118.txt:62
./technical/plos/pmed.0020120.txt:15
./technical/plos/pmed.0020123.txt:271
./technical/plos/pmed.0020140.txt:222
./technical/plos/pmed.0020144.txt:59
./technical/plos/pmed.0020145.txt:33
./technical/plos/pmed.0020146.txt:40
./technical/plos/pmed.0020148.txt:40
./technical/plos/pmed.0020149.txt:41
./technical/plos/pmed.0020150.txt:44
./technical/plos/pmed.0020155.txt:72
./technical/plos/pmed.0020157.txt:15
./technical/plos/pmed.0020158.txt:66
./technical/plos/pmed.0020160.txt:312
./technical/plos/pmed.0020161.txt:217
./technical/plos/pmed.0020162.txt:297
./technical/plos/pmed.0020180.txt:85
./technical/plos/pmed.0020181.txt:77
./technical/plos/pmed.0020182.txt:386
./technical/plos/pmed.0020187.txt:52
./technical/plos/pmed.0020189.txt:37
./technical/plos/pmed.0020191.txt:9
./technical/plos/pmed.0020192.txt:11
./technical/plos/pmed.0020194.txt:55
./technical/plos/pmed.0020195.txt:35
./technical/plos/pmed.0020196.txt:42
./technical/plos/pmed.0020197.txt:64
./technical/plos/pmed.0020198.txt:50
./technical/plos/pmed.0020200.txt:42
./technical/plos/pmed.0020201.txt:43
./technical/plos/pmed.0020203.txt:61
./technical/plos/pmed.0020206.txt:171
./technical/plos/pmed.0020208.txt:70
./technical/plos/pmed.0020209.txt:214
./technical/plos/pmed.0020210.txt:119
./technical/plos/pmed.0020212.txt:167
./technical/plos/pmed.0020216.txt:217
./technical/plos/pmed.0020226.txt:9
./technical/plos/pmed.0020231.txt:92
./technical/plos/pmed.0020232.txt:175
./technical/plos/pmed.0020235.txt:52
./technical/plos/pmed.0020236.txt:53
./technical/plos/pmed.0020237.txt:46
./technical/plos/pmed.0020238.txt:50
./technical/plos/pmed.0020239.txt:54
./technical/plos/pmed.0020242.txt:61
./technical/plos/pmed.0020246.txt:420
./technical/plos/pmed.0020247.txt:133
./technical/plos/pmed.0020249.txt:424
./technical/plos/pmed.0020257.txt:51
./technical/plos/pmed.0020258.txt:37
./technical/plos/pmed.0020268.txt:46
./technical/plos/pmed.0020272.txt:73
./technical/plos/pmed.0020273.txt:49
./technical/plos/pmed.0020274.txt:37
./technical/plos/pmed.0020275.txt:44
./technical/plos/pmed.0020278.txt:31
./technical/plos/pmed.0020281.txt:32
```
Why it is useful:
This command is useful because I am able to get a general vew of the number of times the letter "a" is found in the "./technical/plos/" directory 
### Example 2:
Input and output:
```
$ grep -c "Bush" ./technical/911report/*
    ./technical/911report/chapter-1.txt:2
    ./technical/911report/chapter-10.txt:37
    ./technical/911report/chapter-11.txt:12
    ./technical/911report/chapter-12.txt:1
    ./technical/911report/chapter-13.1.txt:0
    ./technical/911report/chapter-13.2.txt:15
    ./technical/911report/chapter-13.3.txt:1
    ./technical/911report/chapter-13.4.txt:23
    ./technical/911report/chapter-13.5.txt:33
    ./technical/911report/chapter-2.txt:1
    ./technical/911report/chapter-3.txt:10
    ./technical/911report/chapter-5.txt:0
    ./technical/911report/chapter-6.txt:39
    ./technical/911report/chapter-7.txt:0
    ./technical/911report/chapter-8.txt:8
    ./technical/911report/chapter-9.txt:0
    ./technical/911report/preface.txt:0
```
Why it is useful:
The command searches all files in the "./technical/911report/" for instances of the term "Bush" and returns the count of each one.
## Command Line Option 4: grep -n
### Example 1:
Input and output:
```
$ grep -n "Bush" ./technical/911report/chapter-1.txt 
    6:    Tuesday, September 11, 2001, dawned temperate and nearly cloudless in the eastern United States. Millions of men and women readied themselves for work. Some made their way to the Twin Towers, the signature structures of the World Trade Center complex in New York City. Others went to Arlington, Virginia, to the Pentagon. Across the Potomac River, the United States Congress was back in session. At the other end of Pennsylvania Avenue, people began to line up for a White House tour. In Sarasota, Florida, President George W. Bush went for an early morning run.
    564:    In Sarasota, Florida, the presidential motorcade was arriving at the Emma E. Booker Elementary School, where President Bush was to read to a class and talk about education. White House Chief of Staff Andrew Card told us he was standing with the President outside the classroom when Senior Advisor to the President Karl Rove first informed them that a small, twin-engine plane had crashed into the World Trade Center. The President's reaction was that the incident must have been caused by pilot error.
```
Why it is useful:
This command seaches for the term "Bush" in the file ./technical/911report/chapter-1.txt. However the -n option returns the line number in the file.
### Example 2:
Input and output:
```
$ grep -n "Mintie" ./technical/government/Media/A_helping_hand.txt 
    8:Mancy Mintie's Uncommon Good organization pays the school
    18:Mintie.
    19:Mintie, a Claremont resident, made it possible for Ceballos to
    27:Mintie, who turns 48 this month, started Uncommon Good in
    42:jobs and survive on them," Mintie said. "That finding became the
    61:Mintie also started to ask questions about the medical field.
    67:affects children. Mintie noticed that health-care professionals
    71:show March 26, 2001. Mintie received a $100,000 "Use Your Life
    73:awards money to those who help others. Mintie said that all of the
    78:Mintie's religious convictions.
    89:church, Our Lady of the Assumption in Claremont, where Mintie plays
    111:poor. Mintie said she hopes her organization can be a national
    118:serving the poor," Mintie said.
    128:Mintie, her colleagues say, could have made a lot of money in
```
Why it is useful:
This command seaches for the term "Bush" in the file ./technical/government/Media/A_helping_hand.txt. The option also shows all the line numbers for the matching lines.


