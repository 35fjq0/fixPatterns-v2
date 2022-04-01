# Expanding Fix Patterns to Enable Automatic Program Repair
Replication package for the research paper "Automatically Discovering Fix Patterns for Automatic Program Repair".


I. Requirements
---------------
 - [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase7-521261.html)
 - [Defects4J](https://github.com/rjust/defects4j)
 - [Git >= 1.9](https://git-scm.com/downloads)
 - [SVN >= 1.8](https://subversion.apache.org/packages.html)
 - [perl >= 5.0.12](https://www.perl.org/get.html)


II. Description
---------------
Our tool automatically generates fix patterns out of similar fixes and compares the generated fix patterns against a state-of-the-art taxonomy. Our tool splits fixes into smaller, method-level chunks and calculates their similarity. A threshold-based clustering algorithm groups similar chunks, generates fix patterns and finds matches with the state-of-the-art taxonomy. We thematically analyse non-matching clusters and observe new fix patterns that expand the existing taxonomy.

The dataset we use in our evaluation is Defects4J and the taxonomy of fix patterns is a collection of fix patterns from the APR literature found in TBar.

III. Prepare Defects4J Bugs
---------------------------
 1. Download and install Defects4J.
 > ./installD4J.sh
 
 2. Check out bugs and fixes.
 > ./checkoutD4JBugs.sh
     
 These two scripts are adapted from [TBar](https://github.com/TruX-DTF/TBar).

 If you fail to install Defects4J or checkout Defects4J bugs, please check [instructions](https://github.com/rjust/defects4j#steps-to-set-up-defects4j).


 IV. TBar fix patterns
 ---------------------
 
 TBar is a template-based automated program repair tool that applies fix patterns from a taxonomy collected form the APR literature.
 
 For more details about the taxonomy of fix patterns and the TBar tool, please see [publication](https://dl.acm.org/doi/10.1145/3293882.3330577).
 
 For more details about how we automatically match our fix patterns with TBar fix patterns in our evaluation, please see [TBar fix patterns](https://github.com/35fjq0/fixPatterns/blob/main/TBarFixPatterns.md).
 
 V. Generate fix patterns
 ------------------------
 > java -jar fixPatterns.jar <path_to_Defects4J_bugs_and_fixes>
 
 VI. Matching fix patterns
 -------------------------
 > ./matchClusters.sh
 
 VII. Structure of the Directories
 -------------------------------
 ```powershell
  |--- README.md               :  user guidance
  |--- TBar.md                 :  TBar fix patters
  |--- FP_taxonomy             :  a taxonomy of fix patterns
  |--- MatchingFPs             :  matching fix patterns
  |--- UnigramFPs              :  fix patterns generated with unigrams
  |--- NewFPs                  :  new fix patterns on the Sun Tools parser
  |--- NewFPs_JavaParser       :  new fix patterns based on the Java parser
  |--- RankedFPs               :  ranked fix patterns
  |--- installD4J.sh           :  a script to install Defects4J
  |--- checkoutD4JBugs.sh      :  a script to checkout Defects4J bugs and fixes


```

----
