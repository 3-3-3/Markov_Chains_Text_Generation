# Markov_Chains_Text_Generation
Markov Chains and Text Generation
Because the stochastic matrix of the Markov chain is used to predict the future state of a system from the current state, a random sampling process acting as the stochastic matrix can be used to generate pseudo-English text from a sample text. The process for generating text using Markov chains has two steps: first, a stochastic matrix must be formed using words from the sample text. Next, the stochastic matrix must be sampled to produce the pseudo-English text.
The form of the stochastic matrix is an nxn matrix, where n is the number of distinct words in the sample text. For example, if the sample text is: “the dog ate the dog fish,” then it follows that the stochastic matrix would be 4x4, because the sample text has four distinct words. The stochastic matrix can be considered the matrix of a linear transformation which takes a word as an input, and outputs a probability vector that corresponds to the probability distribution that the input will be followed by any other word in the sample text. Of course, a word cannot be input into a transformation of the form T(x) = Ax; however, the word can be encoded as an elementary vector pointing in the direction of ith index of the stochastic matrix, where i is the index corresponding to the input word.
This gives some intuition for how the matrix is actually formed. If each column of the matrix corresponds to a word in the sample text, then each column is the probability vector which describes the probability distribution for what the following word will be. Then, each entry in the probability vector also corresponds to a word in the sample matrix; specifically, each entry is the number of times that the word corresponding with the given probability vector is followed by the word corresponding with the entry in the probability vector, divided–because this represents a probability and not a sum–by the total occurrences of the word corresponding with the probability vector.
Once the matrix is formed, it may be sampled using a random number generator to yield pseudo English which sounds like the sample text, and sounds somewhat like English (of course, if a non-English sample text were provided, that would be that language of the text produced). However, because the stochastic matrix is never updated, the model only considers the preceding word and not the words before that, so the generated text is not all that grammatical. While there are likely other ways to sample from the stochastic matrix, the way I came up with is as follows: first, calculate  a random number between 0 and 1. Then, start summing the entries of the chosen probability vector until the sum is greater than or equal to the randomly generated number. When that condition is met, the index which satisfies the condition is the chosen word, so the next seed is the elementary vector pointing in the direction of the chosen word. This elementary vector can be used to determine the next word, and so on. 
