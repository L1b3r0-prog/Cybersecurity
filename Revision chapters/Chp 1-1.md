Chp 1-1
--------------------------------------------------------------------------------------------------------------
Goals of Cybersecurity
Secrecy
•	Effect of mechanisms used to limit number of principals who can access info such as cryptography and access control
Confidentiality
•	Obligation to protect person/org secrets if you know them
Privacy
•	Ability and/or right to protect personal info and extends to prevent invasions of personal space

What is Security Posture
Solidifying protection system for org security isn’t enough. **Detection and response** must be aligned to enhance overall security posture.
•	Enhancing detection systems to quickly identify attack
•	Enhancing effectiveness of response process to reduce time between infection and containment
Threat landscape
Continuously expanding as orgs allow working flexibility such as Remote access and BYOD
Remote access : using own infrastructure to access company’s resources
BYOD : failures happen because of poor planning and network architecture which leads to insecure implementation
Entry points for end user based on connectivity
1)	Between On-premises and Cloud
2)	Between BYOD devices and Cloud
3)	Between On-premises and BYOD
4)	Between Cloud and Personal devices

Credential
Multi Factor Authentication (MFA)
•	Uses multi factors for authentication such as ID/Password + one time password.
•	OTP is delivered through registered mobile number after user is authenticated
•	Other factors : biometric info (fingerprints, irises, face recog)
Continuous monitoring
•	Continuous authentication is a new tech that uses a person’s behaviour to continuously verify their identity throughout a session and not just at entry point

Security consideration taken for apps
•	Apps developed in-house : measures should be taken to ensure that apps are using secure framework throughout sw dev lifecycle
•	Apps users are paying for service : vendor security and compliance policy should be checked carefully to verify whether company’s security and compliance requirements are met

Cybersecurity Challenges
Top causes of breaches
1)	Malware (viruses and trojans)
2)	Lack of diligence and untrained employees
3)	Phishing and social engineering
4)	Targeted attack
5)	Ransomware
6)	Government-sponsored attack

1,2,3
Correlated to human error. May start with phishing email that uses social engineering to trick employee to download virus, malware or trojan.
4
Attacker has specific target in mind when creating plan of attack. During initial phase, attacker will spend a lot of time and resources to perform public reconnaissance to obtain necessary info to carry out attack
Another attribute is longevity or amount of time to maintain persistent access to the target’s network. Intent is to continue moving laterally across network compromising diff systems until goal is reached
5
 Companies across the world are still failing to implement effective vuln management program
6
Intent to steal info to be used against another party. Private sector shouldn’t ignore these signs.
Orgs invest more into threat intelligence, machine learning and analytics to protect assets

Red and Blue team
Red team performs attack and pens the env against the current security controls aka (pen testing)
Blue team ensures assets are secure and if Red team finds a vuln and exploits it, they need to rapidly remediate and doc it as parts of the lesson learned
Red team is composed of highly trained indv with diff skill sets and must be aware of the current threat landscape, trends and understand how current attacks are taking place
Must also have coding skills to create their own exploit and customize it to exploit relevant vulns
Metrics of Red Team
Mean Time to Compromise (MTTC): starts counting from the minute that RT initiated the attack to the moment target is successfully compromised
Mean Time to Escalate (MTPE): starts at the same point as the previous metric but goes all the way to full compromise, which is the moment that RT has admin priv on target

Metrics of Blue Team
Estimated Time to Detection (ETTD)
Estimated Time to Recovery (ETTR)
Save evidence: to ensure there are tangible info to analyse, rationalise and take action to mitigate in the future
Validate the evidence:  not every alert or evidence will lead to valid attempt to breach system. But if it does, has to be catalogued as Indication of Compromise (IoC)
Engage whoever is necessary to engage: BT must know what to do with IoC and which team should be aware of this compromise.
Triage incident: may need to engage law enforcement or need a warrant to perform further investigation where a proper triage will help on this process
Scope the breach: BT will have enough info to do this
Create remediation plan: BT should put tgt a plan to either isolate or evict adversary
Execute the plan and recover from the breach	
