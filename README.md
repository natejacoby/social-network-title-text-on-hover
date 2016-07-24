# social-network-title-text-on-hover

This was a little something I've found myself using on the last few projects, so I wrote a quick script to do it. Super simple, but I enjoyed the problem solving behind it as a n00b.



###Your HTML(.._cough_ erb) might look like this:
```
<div class="your-image-container">
  <%= link_to "#{image_tag('social-1.png', 'data-text': 'Twitter')}".html_safe, 'https://www.twitter.com' %>
  <%= link_to "#{image_tag('social-2.png', 'data-text': 'LinkedIn')}".html_safe, 'https://www.linkedin.com' %>
  <%= link_to "#{image_tag('social-3.png', 'data-text': 'Github')}".html_safe, 'https://www.github.com' %>
  <%= link_to "#{image_tag('social-4.png', 'data-text': 'Gitlab')}".html_safe, 'https://www.gitlab.com' %>
 
  <div class="the-div-you-want-the-text-output">
    <!-- Your Output will Appear Here-->
  </div>
</div>
```
 The important thing to remember is the 'data-text' portion of the element. 
 
####In regular HTML5 it would be:
 
 ```
 <img src="images/social-1.png" data-text="Twitter" />
 ```
###In a \<script> tag or a .js file
```
    var $image = $('.your-image-relative-path img');

    $.each($image, function () {

        var $container = $('.the-div-you-want-the-text-output');

        $(this).mouseenter(function () {
            var $text = $(this).attr("data-text");

            $container.hide().html('<p>' + $text + '</p>').fadeIn(100);
        }). mouseleave(function() {
            $container.fadeOut(60)
        })
    });
