# Assessment of the Floquet--Koopman Numerical Experiments

## Overall conclusion

All six experiments are consistent with the theoretical predictions for the diffusive Stuart--Landau benchmark. The numerical chain

\[
\text{Floquet mode}
\longrightarrow
\chi_m
\longrightarrow
\psi_m
\longrightarrow
D\psi_m
\longrightarrow
z_\theta^n\psi_m
\]

behaves as expected, and the two forward-only consistency tests show the predicted geometric convergence toward return-choice and entry-time independence.

The evidence is strongest for:

1. verification of the spectral hypotheses;
2. convergence of the return-map construction of \(\chi\);
3. identification of \(D\psi\) with the slow adjoint Floquet covector;
4. direct consistency of forward suspension and forward globalization.

The continuous-time residual and spectral-ladder figures are also correct, but part of their behavior follows algebraically from how the observables are constructed. They should therefore be presented as theorem-oriented consistency tests rather than independent discoveries of Koopman structure.

The benchmark is deliberately transparent: in the co-rotating frame the periodic orbit becomes an equilibrium and the Floquet spectrum is explicit. This makes it an excellent calibration example for the theory, although not a stress test of every possible time-dependent or nonnormal Floquet geometry.

## Summary table

| Experiment | Principal theoretical target | Quantitative outcome | Assessment |
|---|---|---|---|
| 1. Floquet spectrum | spectral hypotheses and unique slow multiplier | phase-branch exponent errors below \(8\times10^{-10}\); worst displayed high-frequency radial error about \(2.01\times10^{-4}\) | Strong verification of assumptions |
| 2. Section eigenfunction limit | \(\chi_m\to\chi\), \(\chi\circ P=\mu_\star\chi\) | final relative errors at return depth 10 between \(2.81\times10^{-10}\) and \(4.75\times10^{-9}\); late reduction factor about \(0.2213\) | Strong nonlinear convergence evidence |
| 3. Koopman eigenfunction residual | \(\psi(\Phi^tW)=e^{\lambda_\star t}\psi(W)\) | maximum residuals \(9.31\times10^{-8}\), \(1.90\times10^{-6}\), and \(1.30\times10^{-5}\) | Correct; strongest information is the small gluing defect at crossings |
| 4. Derivative alignment | \(D\psi|_\Gamma\) equals the selected adjoint Floquet covector | maximum directional-derivative error \(8.07\times10^{-9}\) | Strong normalization and mode-identification check |
| 5. Koopman eigenvalue lattice | \(z_\theta^n\psi\) has exponent \(\lambda_\star+in\omega_0\) | maximum real-part error \(5.28\times10^{-7}\); imaginary-part error at machine precision | Correct forward ladder construction |
| 6a. Return-choice independence | forward suspension is independent of the chosen future return | error at depth 8 from \(1.15\times10^{-10}\) to \(1.19\times10^{-8}\); reduction factor \(0.22136\) | Direct, strong support for the forward-suspension lemma |
| 6b. Entry-time independence | basin-wide extension is independent of admissible entry time | later-return errors at depth 8 are \(3.77\times10^{-9}\) and \(4.60\times10^{-9}\); reduction factor \(0.22136\) | Direct, strong support for the forward-globalization lemma |

## Experiment 1: Floquet spectrum and the unique slow multiplier

### Theoretical statement tested

The theoretical framework assumes an attracting periodic orbit with one neutral phase direction and a simple, isolated, unique slow transverse Floquet multiplier. For the benchmark,

\[
\lambda_\star=-d\left(\frac{\pi}{L}\right)^2=-0.12,
\qquad
\mu_\star=e^{\lambda_\star T}\approx0.47048922.
\]

### Numerical outcome

The numerically recovered phase branch agrees extremely closely with the exact exponents:

- neutral phase mode: absolute exponent error approximately \(7.96\times10^{-10}\);
- slow \(n=1\) phase mode: approximately \(3.82\times10^{-10}\);
- \(n=2\) phase mode: approximately \(2.05\times10^{-10}\);
- \(n=3\) phase mode: approximately \(1.26\times10^{-10}\).

The radial exponents also agree. The largest displayed error, approximately \(2.01\times10^{-4}\), occurs for the fastest plotted radial mode, whose one-period multiplier is only about \(3.94\times10^{-9}\). Recovering an exponent from such a tiny multiplier is necessarily more sensitive to finite-difference and time-integration error.

### Assessment

The experiment clearly confirms:

- one neutral phase exponent;
- strict transverse stability;
- simplicity and isolation of \(\lambda_\star=-0.12\);
- separation of the slow mode from the faster phase and radial branches.

This experiment verifies the assumptions of the main theorem rather than a new theorem itself. Its role in the paper is essential and correctly scoped.

## Experiment 2: Convergence of the section eigenfunction

### Theoretical statement tested

On the phase section, the normalized eigenfunction is constructed through the slow-mode return limit

\[
\chi_m(z)=\mu_\star^{-m}p(P^mz).
\]

The target relation is

\[
\chi(Pz)=\mu_\star\chi(z).
\]

### Numerical outcome

Using a twelve-return value as the numerical reference, the relative errors at return depth 10 are:

| Initial state | Initial relative error | Relative error at depth 10 | Late reduction factor |
|---|---:|---:|---:|
| Near cycle | \(2.77\times10^{-2}\) | \(2.81\times10^{-10}\) | approximately \(0.2213\) |
| Moderate | \(5.61\times10^{-2}\) | \(1.66\times10^{-9}\) | approximately \(0.2213\) |
| Farther in basin | \(9.36\times10^{-2}\) | \(4.75\times10^{-9}\) | approximately \(0.2213\) |

The nearly identical reduction factor across all three initial conditions indicates a common asymptotic error mechanism, as expected from the spectral gap beyond the selected slow mode.

### Assessment

This is one of the strongest nonlinear tests in the notebook. It shows stable geometric convergence for states at several distances from the periodic orbit and supplies the numerical input needed by the subsequent forward-suspension construction.

The reference is a high-return numerical approximation rather than a separately known closed-form nonlinear eigenfunction. Thus the plot demonstrates internal convergence of the return-limit sequence, not an exact error against an independent analytic formula. That is appropriate for the intended theorem-verification role.

## Experiment 3: Koopman eigenfunction residual

### Theoretical statement tested

The principal Koopman eigenfunctional should satisfy

\[
\psi(\Phi^tW_0)=e^{\lambda_\star t}\psi(W_0).
\]

The notebook evaluates a normalized residual using the finite-return approximation \(\psi_m\).

### Numerical outcome

The maximum residuals are:

| Initial state | Maximum residual |
|---|---:|
| Near cycle | \(9.31\times10^{-8}\) |
| Moderate | \(1.90\times10^{-6}\) |
| Farther in basin | \(1.30\times10^{-5}\) |

The residual increases with distance from the periodic orbit, as expected for a fixed finite return depth. Between section crossings it is near roundoff, while small jumps appear at crossings.

### Assessment

The result is fully consistent with the theorem. Its interpretation must nevertheless be precise:

- between crossings, the exponential law is built into the suspension formula;
- the nontrivial information is the mismatch when finite-return representatives are changed across a section crossing;
- those jumps quantify the gluing defect caused by replacing \(\chi\) with \(\chi_m\).

Thus the experiment supports the local and basin-wide Koopman eigenfunction equations, but it should not be described as an entirely independent recovery of the exponential law. Experiment 6 gives the more direct test of the distinctive forward-only claims.

## Experiment 4: Derivative--Floquet correspondence

### Theoretical statement tested

Along the periodic orbit, the derivative of the nonlinear eigenfunctional should equal the chosen adjoint Floquet covector. Under the selected normalization, the first imaginary cosine direction has derivative one and all tested radial and faster phase directions have derivative zero.

### Numerical outcome

The numerical derivative in the selected direction is

\[
0.9999999919341513,
\]

with absolute error approximately

\[
8.07\times10^{-9}.
\]

All other tested components are zero to approximately \(10^{-14}\) or smaller, except for harmless roundoff-level values.

### Assessment

The experiment strongly confirms the normalization and the identification of the nonlinear observable with the intended Floquet mode. Because the seed observable is deliberately aligned with this mode, the experiment is best interpreted as a stringent consistency and implementation check, not as blind mode discovery.

It directly supports the derivative--Floquet correspondence used to identify \(\psi\) as the nonlinear continuation of the selected linear amplitude.

## Experiment 5: Floquet--Koopman Koopman eigenvalue lattice

### Theoretical statement tested

For the phase eigenfunction \(z_\theta\), the observables

\[
\psi_n=z_\theta^n\psi,
\qquad n\in\mathbb Z,
\]

should satisfy

\[
\psi_n(\Phi^tW)
=
 e^{(\lambda_\star+in\omega_0)t}\psi_n(W).
\]

### Numerical outcome

For \(n=-2,-1,0,1,2\):

- the maximum error in the estimated real part is approximately \(5.28\times10^{-7}\);
- the maximum error in the imaginary part is approximately \(2.22\times10^{-16}\).

All five recovered exponents lie on the predicted vertical ladder with common real part \(-0.12\) and frequencies shifted by integer multiples of \(\omega_0=1\).

### Assessment

The experiment accurately verifies the forward product construction of the ladder. The imaginary shifts are especially precise because the phase factor is explicitly used in forming the observable.

The experiment does not test the stronger converse statement that every normalized principal eigenfunctional associated with the same period-map multiplier must be of the form \(z_\theta^n\psi\). That classification is an analytical consequence of uniqueness and is not realistically provable by finite numerical data.

## Experiment 6a: Independence of the selected future return

### Theoretical statement tested

The forward-suspension formula should be independent of whether one uses the next section hit or waits one or two additional periods:

\[
\psi^{[q]}(W)
=
 e^{-\lambda_\star(\tau(W)+qT)}
 \chi\!\left(\Phi^{\tau(W)+qT}W\right),
\qquad q=0,1,2.
\]

For the finite-return approximation \(\chi_m\), the discrepancy should tend to zero as \(m\) increases.

### Numerical outcome

| Initial state | Error at depth 0 | Error at depth 8 | Median reduction factor |
|---|---:|---:|---:|
| Near cycle | \(2.0042\times10^{-5}\) | \(1.1487\times10^{-10}\) | \(0.22136\) |
| Moderate | \(3.5525\times10^{-4}\) | \(2.0263\times10^{-9}\) | \(0.22136\) |
| Farther in basin | \(2.0982\times10^{-3}\) | \(1.1915\times10^{-8}\) | \(0.22136\) |

### Assessment

This experiment directly targets one of the paper's principal new semiflow ingredients. All three cases show clean geometric decay, with the same reduction factor observed in the section-limit experiment.

The agreement of these rates is theoretically meaningful: the return-choice defect reduces to differences between finite-return approximations of the same section eigenfunction. Therefore

\[
\chi_m\to\chi
\quad\Longrightarrow\quad
\psi_m^{[q]}-\psi_m^{[0]}\to0.
\]

The results provide strong numerical corroboration of return-number independence in the forward-suspension and gluing lemma.

## Experiment 6b: Independence of the globalization entry time

### Theoretical statement tested

Once a trajectory enters the local tube, the basin-wide candidate

\[
G_m(t_j)
=
 e^{-\lambda_\star t_j}
 \psi_m^{\mathrm{loc}}(\Phi^{t_j}W_0)
\]

should converge to a value independent of the admissible entry time \(t_j\).

### Numerical setup

The local tube is defined by

\[
d_\Gamma(Z)\leq0.14.
\]

The trajectory first enters at

\[
\frac{t_{\mathrm{ent}}}{T}\approx1.010,
\qquad
d_\Gamma(Z(t_{\mathrm{ent}}))\approx0.139198.
\]

Additional entry-time shifts of \(0.40T\), \(1.20T\), and \(2.15T\) are tested.

### Numerical outcome

| Entry-time shift | Error at depth 0 | Error at depth 8 | Median reduction factor |
|---|---:|---:|---:|
| \(0.40T\) | \(1.56\times10^{-16}\) | \(5.58\times10^{-15}\) | roundoff/time-stepping floor |
| \(1.20T\) | \(6.52\times10^{-4}\) | \(3.77\times10^{-9}\) | \(0.22136\) |
| \(2.15T\) | \(7.97\times10^{-4}\) | \(4.60\times10^{-9}\) | \(0.22136\) |

The \(0.40T\) choice shares the same next future section as the first entry and therefore agrees already at finite return depth, up to time-integration accuracy. The later choices use later section representatives and converge geometrically to the same basin-wide value.

### Assessment

This is the most direct numerical test of the forward-globalization lemma. It confirms that the finite-return dependence on the entry time disappears at precisely the same asymptotic rate as the section-limit error.

The calculation uses only positive times, matching the defining distinction between the proposed parabolic-semiflow theory and inverse-flow constructions.

## Relationship between Experiments 2 and 6

A particularly strong feature of the results is the common reduction factor:

\[
0.2213\text{--}0.22136.
\]

This factor appears in:

- convergence of \(\chi_m\) in Experiment 2;
- return-choice independence in Experiment 6a;
- entry-time independence for later returns in Experiment 6b.

This is the predicted proof mechanism, not merely a repeated empirical number. Both choice-independence defects reduce to finite-return tails of the section eigenfunction construction. The numerical results therefore reproduce the logical implication

\[
\chi_m\to\chi
\Longrightarrow
\text{forward-suspension consistency}
\Longrightarrow
\text{forward-globalization consistency}.
\]

## Coverage of the proposed theory

### Directly or substantially corroborated

The experiments cover all principal constructive statements that are naturally testable numerically:

- identification of the unique slow transverse Floquet multiplier;
- convergence of the section eigenfunction construction;
- the continuous-time exponential evolution law;
- derivative alignment with the selected adjoint Floquet mode;
- the forward construction of the Koopman eigenvalue lattice;
- independence from the chosen future section return;
- independence from the chosen globalization entry time;
- exclusive use of positive-time evolution.

### Only indirectly supported

The following are illustrated but not established numerically:

- smooth gluing across an arbitrary phase atlas;
- validity throughout the complete infinite-dimensional basin rather than for sampled trajectories;
- stability of the construction outside the special symmetry class used by the benchmark.

### Not suitable for numerical proof

The following must remain analytical results:

- conditional uniqueness of the eigenfunctional;
- Fréchet \(C^r\) regularity on an infinite-dimensional basin;
- existence for every basin state;
- the converse spectral-branch classification;
- nonexistence of a global real scalar eigenfunctional for a negative multiplier;
- the real double-cover and deck-odd classification.

The current benchmark has a positive slow multiplier, so the negative-multiplier theorem is intentionally not included in the numerical tests.

## Final assessment for paper use

The numerical section is now well aligned with the planned theory. It does not merely verify the old Floquet input: Experiments 6a and 6b directly test the two forward-only identities that distinguish the proposed parabolic-semiflow construction.

The appropriate claim in the paper is:

> The computations corroborate the constructive Floquet--Koopman identities, including return-choice and entry-time independence, in a diffusive Stuart--Landau reaction--diffusion benchmark with an explicitly known attracting cycle and Floquet spectrum.

The paper should not claim that the figures prove uniqueness, infinite-dimensional smoothness, global existence on the entire basin, or the negative-multiplier topological obstruction. Subject to that wording, the numerical results conform very well to the theory they are intended to support and are sufficient for a proof-centered paper.
