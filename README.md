# Probabilistic_Graphic_Model

HW1 - Intro to Bayesian Network
   - draw basic BN using SAINAM
   - factor product and marginalization using Octave
   - When an evidence is observe, reduce all the other assignment if evidence not holds
   - joint distribution
   - marginal over a given set of variables
 
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
