Results Interpretation

The output of the Shor’s algorithm implementation consists of measurements from the phase estimation register, followed by rational approximations used to infer the period 
𝑟
r, and finally the recovered factors of 
𝑁
N.

Phase Register Measurements

Each measurement of the phase register is an 8-bit binary string. Interpreting this value as an integer and dividing by 
2
8
=
256
2
8
=256 yields a measured phase in the interval 
[
0
,
1
)
[0,1). These phases approximate values of the form 
𝑘
/
𝑟
k/r, where 
𝑟
r is the unknown period of the modular exponentiation function.

Due to the probabilistic nature of quantum phase estimation and the finite number of phase qubits, the measured phases are noisy and distributed across multiple rational approximations. As a result, individual measurements should not be interpreted in isolation.

Continued Fraction Analysis

Each measured phase is converted into a rational approximation using continued fractions. The denominator of this fraction provides a candidate guess for the period 
𝑟
r. Across many runs, multiple candidate periods appear, including incorrect values and integer multiples of the true period.

The correct period is identified by:

Repeated appearance of the same small denominator across different measurements

Successful verification via modular exponentiation

In the observed results, small candidate values such as 
𝑟
=
4
r=4 and its multiples appear frequently, while larger denominators occur sporadically and are attributed to measurement noise.

Successful Period Identification

In a representative run, the phase register measured the binary value 01000000, corresponding to a phase of exactly 
0.25
=
1
/
4
0.25=1/4. This yields an unambiguous period estimate of 
𝑟
=
4
r=4, demonstrating a high-confidence result from the phase estimation step.

Factor Extraction

Once a valid period 
𝑟
r is identified, classical post-processing is applied by computing:

gcd
⁡
(
𝑎
𝑟
/
2
±
1
,
𝑁
)
gcd(a
r/2
±1,N)

For the identified period 
𝑟
=
4
r=4, this step successfully returns the non-trivial factors:

[
3
,
5
]
[3,5]
Summary

These results demonstrate that the implementation correctly performs:

Quantum phase estimation with finite precision

Rational reconstruction of candidate periods

Period validation via classical checks

Final factor extraction

The presence of multiple candidate periods is expected and reflects realistic quantum measurement behavior rather than implementation error. Correct factors emerge when the inferred period is both valid and even, confirming the correctness of the overall Shor’s algorithm pipeline.