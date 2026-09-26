My polars titlecase PR failed CI with E0597/E0521 while local cargo check
passed. The difference: I wrote transmute::<&'a str, &'a str>(slice) where the
original wrote transmute::<&str, &'a str>(slice). Writing the SOURCE type as
&'a str told borrowck "this reference already has the right lifetime" — so it
actually checked it, and the dangling borrow was real.

Local verification lesson: cargo check -p crate is not enough when the code is
behind a cargo feature flag — my function was never compiled locally. Always
compile with the feature flags CI uses.
