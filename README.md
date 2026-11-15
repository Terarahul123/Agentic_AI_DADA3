# DADA3: A bug-fixing team

**Deployed app:** https://bug-fixing-team-mnni.onrender.com/

## Write-up

### Setup

 Model: Gemini gemini-3.5-flash-lite, Sandbox: Daytona, two runs of each system, Nothing changed from the bundle.

### Results

team  :        resolved 8/10, triage 10/10, bugs fixed 5/7, false claims 2, 145 calls, 4,406,016 tokens, 1262 s.            
baseline:      resolved 8/10, triage 10/10, bugs fixed 5/7, false claims 2, 41 calls, 418,584 tokens, 138 s.           
team (2) :     resolved 10/10, triage 10/10, bugs fixed 7/7, false claims 0, 96 calls, 1,919,729 tokens, 414 s.          
baseline (2):  resolved 9/10, triage 10/10, bugs fixed 6/7, false claims 1, 55 calls, 608,024 tokens, 176 s.    

### Did the team do better?
Yes, but not by much. The first run was tied and the team was a little bit better than the baseline in the 2nd run by 1 issue and 1 false claim. But the team's own two runs differed by two issues, so the gap between systems is smaller than the noise between runs.

### The handoff
The only handback was on #2 in the first team run. The verifier said split_amount(-1000, 3) gave [-335, -334, -334] instead of [-334, -333, -333] and it was right. The next fix still didn't pass. It gave [-333, -333, -334], and the verifier accepted it because its new test expected that value instead of the docstring's. The hidden tests caught it

### What did it cost?
The team used 2 to 3.5 times the calls and 3 to 10 times the tokens of the baseline. For one extra resolved issue across two runs, it's not worth it here, especially since the team's false claims came from weak verifier tests, the exact thing the split was supposed to fix.
