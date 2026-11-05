# econ3916-lab13-multivariate-ols
# Multivariate OLS — What "Controlling For" Actually Does

## Objective
I used simulated data with a known truth to see what adding a control to a regression actually does, when it removes bias, and when it creates it.

## Methodology
- Simulated wages that depend on education and on an unobserved ability term, then compared a regression that leaves ability out with one that includes it.
- Predicted the omitted-variable bias with the formula gamma × delta and compared it with the actual bias.
- Recovered the multivariate coefficient on education in three steps (Frisch-Waugh-Lovell): I regressed the part of wages that ability does not explain on the part of education that ability does not explain.
- Simulated two independent variables that both cause a third, then added that third variable (a collider) as a control.
- Simulated two nearly identical regressors and used variance inflation factors to separate what multicollinearity damages from what it leaves alone.
- Fitted a regression with an interaction term so the return to experience could differ between union and non-union workers.
- Asked an AI to write a function that builds a specification table, checked its coefficients and standard errors against my own regressions, and revised my prompt once.

## Key Findings
- Leaving ability out gave a return to education of 5,126, about twice the true 2,500. Putting ability in gave 2,546.
- The bias formula predicted a bias of 2,629, and the actual bias was 2,626.
- The three-step Frisch-Waugh-Lovell method gave exactly the same coefficient as the full regression, so "controlling for" a variable means partialling it out.
- The collider control turned a true effect of zero into an estimate of -0.596, with a p-value that printed as 0.000. The regression without the control was the right one.
- Multicollinearity made the standard errors about 12 times larger, but it did not bias the estimates.
- A year of experience was worth 903 to non-union workers and 504 to union members.
- The AI's first version matched my coefficients but not my standard errors, because it used robust standard errors without being asked. After I specified classical standard errors in the revised prompt, every number matched.
