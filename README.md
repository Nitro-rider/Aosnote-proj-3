# Aosnote-proj-3
CI/CD project terraform and codebuild
Runs an simple website which is linked to a github account and whenever changes are made to the (terrafrom) code a CI/CD pipeline will be triggered to perform a test build.

I had trouble starting my build in AWS. I had previously copied and pasted a reference file, then filled in all necessary fields, specifically talking about the buildspec.yml file. Although i direct copied the reference template file, i kept getting an error and the build would fail and exit.

[Container] 2024/06/24 15:54:11.969767 Phase complete: DOWNLOAD_SOURCE State: FAILED
[Container] 2024/06/24 15:54:11.969792 Phase context status code: YAML_FILE_ERROR Message: Expected Commands[0] to be of string type: found subkeys instead at line 10, value of the key tag on line 9 might be empty

The yaml file error was the source of the problem and eventually, to solve this, I verified my yaml file using the online yaml verifier "yamllint.com". yamllint validated the code and must have performed a "fmt" behind the scene. I am guessing there was a problem with indentation because i could not pick up any visible changes made by yamllint. I took the validated code pasted it in my "buildspec.yml" file and everything worked perfectly. 

I believe it would be very beneficial to incorperate some kind of linter for yaml files to pass through before being used in builds to reduce time looking for bugs. There may be possible linters for all kinds of things so further investigation is needed on this subject in the near future. 
