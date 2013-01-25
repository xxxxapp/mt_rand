mt_rand
=======

Mersenne Twister pseudorandom number generator

enhancements:
Lock-free for thread-safe use with little performance loss;

History:
This code comes from http://www.math.sci.hiroshima-u.ac.jp/~m-mat/MT/emt.html.
Mersenne Twister(MT) is a pseudorandom number generating algorithm developped by Makoto Matsumoto and Takuji Nishimura (alphabetical order) in 1996/1997. An improvement on initialization was given on 2002 Jan. 
MT has the following merits:
It is designed with consideration on the flaws of various existing generators.
The algorithm is coded into a C-source downloadable below.
Far longer period and far higher order of equidistribution than any other implemented generators. (It is proved that the period is 2^19937-1, and 623-dimensional equidistribution property is assured.)
Fast generation. (Although it depends on the system, it is reported that MT is sometimes faster than the standard ANSI-C library in a system with pipeline and cache memory.) (Note added in 2004/3: on 1998, usually MT was much faster than rand(), but the algorithm for rand() has been substituted, and now there are no much difference in speed.)
Efficient use of the memory. (The implemented C-code mt19937.c consumes only 624 words of working area.)

Here we don't want to go into a detailed discussion. For detail, please consult with the preprint mt.ps. Briefly saying, MT is designed according to the modern researches on the practical conditions which a generator should satisfy. We don't have a practical definition of "good pseudorandomness" for pseudorandom number generators yet now. So, there is no rigourous mathematical assurance for MT to be a defect-free random number generators. 

However, it is widely believed that the spectral test is one of the strongest test to select a good generator. MT is designed to pass a similar test, called the k-distribution test. For example, if we look the output with 32-bit accuracy, then the 623-tuples from the output in a whole period are equidistributed in the 623-dimensional unit cube. For 16-bit accuracy, 1246-tuples are equidistributed in 1246-dimension, and for 2-bit accuaracy, in 9968-dimension. These values are at least 15 times larger than the previous records. MT passed many stringent tests, including the diehard test by G.Marsaglia and the load test by P.Hellekalek and S.Wegenkittl. 

MT is an improved version of a very successful generator TT800, which has the period 2^800-1 and has been used for a few years with favorable comments by many users. MT is much more robust. 

The generator is implemented to generate the output only by fastest arithmetic operations: no division, no multiplication. By generating an array at one time, it takes the full advantage of cache memory and pipeline processing. 
