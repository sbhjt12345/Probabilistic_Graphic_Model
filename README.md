# Probabilistic_Graphic_Model

HW1 - Intro to Bayesian Network
   - draw basic BN using SAINAM
   - factor product and marginalization using Octave
   - When an evidence is observe, reduce all the other assignment if evidence not holds
   - joint distribution
   - marginal over a given set of variables
   
   factorization is one way to represent a BN by its CPDs.
 
HW2 - Genetic Inheritance
   - phenotypeGivenGenotypeMendelianFactor: output only be 0 or 1, meaning showing the physical trait or not
   - phenotypeGivenGenotypeFactor: difference with above is now an alphalist is given to compute the probability of showing a physical trait
   - genotypeGivenAlleleFreqsFactor:given frequencies of alleles, compute certain probability of genotype(FF,Ff,ff)
   - genotypeGivenParentsGenotypesFactor: given parent genotype, compute child genotype probability
   - constructGeneticNetwork: combine aboves
   
   - phenotypeGivenCopiesFactor: getting only one allele from each parent, compute the probability of showing a certain physical trait. (Note that allele could >2)
   - constructDecoupledGeneticNetwork: construct BN using the idea above, for every dude in the list
   
   - constructSigmoidPhenotypeFactor: using sigmoid function to compute the probability of showing a certain physical trait
      meaning dude get two genes from parents, decouple each of them, with each allele in each gene has a corresponding weight representing how much it could affect the final result. (eg. weight= 3 meaning it could quite lead to getting the final physical trait to be shown, while weight=-3 means just the opposite) and z=(sum) of all those weight*(binarys). then apply sigmoid function to get the result, which is the value.
      
      - The data structure for the HW is
         var : phenotype variable, genotype variable1, genotype variable2,....
         cardinality: 2, 3, 3, ...
         val :   FF FF 1 val(probability)
                 FF FF 0 val(probability)
                 FF Ff 1 val
                 FF Ff 0 val
                 ...
                 ...
       - And the genetic network is just applying the above DS to a family tree


HW3 - Behind Schedule! Finish tmr
       This HW implements simple OCR to do handwritting recognition.
       The idea is the factor of (I,C) where I is the image of the character which is represented by a pixel marix, and C is the actual character. I is always observed; and another factor is (C(i),C(i+1)) which is the connection between adjacent characters.
       
      -Compute Singleton Markov Network: (I,C) factor is the baseline for OCR. this matlab file implemented the job. Logistic Regression is used( as learned in machine learning course), but the code is not sth I familiar with in the ML course.
      
      -Compute Pairwise factor: outputs the struct array containing all (C i,C i+1) factors
      -Compute Triplet factor: just like pairwise, but scope now has three variables
      - Compute Similarity: given images, compute how similar two images of characters are
      - Compute All Similarity: given all the data, compute similarity between any two characters(images)
      - Compute TopSimilarity: only output first F factors with highest similarities
