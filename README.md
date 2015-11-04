# remCalc
Sass mixin to create rem values based on px input for an arbitrary property

# usage

    @include remCalc(padding, 23 16);
    @include remCalc(font-size, 20);
    @include remCalc(margin, 40 30 20 50, !important);
