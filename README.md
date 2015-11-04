# remCalc
Sass mixin to create rem values based on px input for an arbitrary property

#mixin
@mixin remCalc($property, $sizeValues, $important:"") {

  $pixels: "";
  $rems: "";

  @each $value in $sizeValues {

    @if $value != 0 and $value != auto and $value != inherit {
      // iterate each value that isn't 0, auto, inherit and add to var
      $pixels : #{$pixels + " " + $value + px};
      $rems : #{$rems + " " + $value / 10 + rem};
    }

    @else {
      // if value is 0 or auto output as is
      
      $pixels: #{$pixels + " " + $value};
      $rems: #{$rems + " " + $value};
    }

  }

  @if $important == !important {
    // check !important flag and add to var
    
    $pixels: #{$pixels + " " + !important};
    $rems: #{$rems + " " + !important};
  }

  //Finally Output the values
  
  #{$property}: $pixels;
  #{$property}: $rems;

}

# usage

    @include remCalc(padding, 23 16);
    @include remCalc(font-size, 20);
    @include remCalc(margin, 40 30 20 50, !important);
