/*-------------------------------------------------------------------------------------------------------------------------------*/
/*This is main JS file that contains custom style rules used in this template*/
/*-------------------------------------------------------------------------------------------------------------------------------*/
/* Template Name: "Modesto"*/
/* Version: 1.0 Initial Release*/
/* Build Date: 06-02-2016*/
/* Author: LionStyle*/
/* Website: http://moonart.net.ua/modesto/ 
/* Copyright: (C) 2016 */
/*-------------------------------------------------------------------------------------------------------------------------------*/

/*--------------------------------------------------------*/
/* TABLE OF CONTENTS: */
/*--------------------------------------------------------*/
/* 01 - VARIABLES */
/* 02 - page calculations */
/* 03 - function on document ready */
/* 04 - function on page load */
/* 05 - function on page resize */
/* 06 - function on page scroll */
/* 07 - swiper sliders */
/* 08 - buttons, clicks, hovers */


$(function() {

    "use strict";

    /*================*/
    /* 01 - VARIABLES */
    /*================*/
    var swipers = [], winW, winH, winScr, footerTop, _isresponsive, _ismobile = navigator.userAgent.match(/Android/i) || navigator.userAgent.match(/webOS/i) || navigator.userAgent.match(/iPhone/i) || navigator.userAgent.match(/iPad/i) || navigator.userAgent.match(/iPod/i), htmlVal = $('html'), headerVal = $('header');

    /*========================*/
    /* 02 - page calculations */
    /*========================*/
    function pageCalculations(){
        winW = $(window).width();
        winH = $(window).height();
        footerTop = ($('footer').length)?$('footer').offset().top : 0;
        if($('.portfolio-detail-related-entry').length) footerTop = $('.portfolio-detail-related-entry').offset().top;
        if($('.is-mobile').is(':visible')) _isresponsive = true;
        else _isresponsive = false;
        $('.page-height').css({'height':winH, 'min-height':(winH<480)?480:winH});
        if(winH<=600) $('body').addClass('min-height');
        else $('body').removeClass('min-height');
        $('.rotate').each(function(){
            $(this).css({'width':$(this).parent().height()});
        });

        /*flex align - fix IE*/
        if(!_isresponsive){
            $('.flex-js').each(function(){
                if(winH<$(this).height()){
                    $(this).css('height','100%');    
                }else{
                    $(this).css('height',winH); 
                }
            });
        }   
        /*flex align - fix IE*/
    }

    /*=================================*/
    /* 03 - function on document ready */
    /*=================================*/
        //loader
        $('#loader-wrapper').fadeOut(300);



    $('.input').each(function(){
        if($(this).val()!=='') $(this).parent().addClass('focus');
    });
    if(_ismobile) $('body').addClass('mobile');
    pageCalculations();

    /*============================*/
    /* 04 - function on page load */
    /*============================*/
    $(window).on('load', function(){

        initSwiper();

        $('body').addClass('loaded');
            setTimeout(function(){
                pageCalculations();
            },0);

        
        /*isotope*/    
        if($('.grid').length > 0){
            var $grid = $('.grid').isotope({
              itemSelector: '.grid-item',
              masonry: {
                columnWidth: '.grid-sizer'
              }
            });

            $('.sorting-menu li').on('click',function(){
                if($(this).hasClass('active')) return false;
                $(this).parent().find('.active').removeClass('active');
                $(this).addClass('active');
                var filterValue = $(this).attr('data-filter');
                $grid.isotope({ filter: filterValue });
                var sorting_menu_btn = $('.sorting-menu .button-drop a span');
                sorting_menu_btn.text($(this).data('name'));
                return false;
            });
        };

        /*lightbox*/
        if($('.lightbox').length > 0){
            $(function(){
                var lightbox = $('.lightbox').simpleLightbox({
                    disableScroll: false
                });
            });
        }
        

    });


    /*==============================*/
    /* 05 - function on page resize */
    /*==============================*/
    function resizeCall(){
        pageCalculations();
    }
    if(!_ismobile){
        $(window).resize(function(){
            resizeCall();
        });
    } else{
        window.addEventListener("orientationchange", function() {
            resizeCall();
        }, false);
    }

    /*==============================*/
    /* 06 - function on page scroll */
    /*==============================*/
    $(window).scroll(function(){
     if ($('.swiper-style-banner').length){
        if ($(this).scrollTop() >= winH){  
            headerVal.addClass('fixed');
        }
        else{
            headerVal.removeClass('fixed');
        } 
     }else{
         headerVal.addClass('fixed');
     }
        

    });


    /*=====================*/
    /* 07 - swiper sliders */
    /*=====================*/

    function initSwiper(){
        var initIterator = 0;
        $('.swiper-container').each(function(){                               
            var $t = $(this);                                 

            var index = 'swiper-unique-id-'+initIterator;

            $t.addClass('swiper-'+index+' initialized').attr('id', index);
            $t.find('.swiper-pagination').addClass('swiper-pagination-'+index);

            if($t.find('.swiper-button').length>=1){
                $t.find('.swiper-button-prev').addClass('swiper-button-prev-'+index);
                $t.find('.swiper-button-next').addClass('swiper-button-next-'+index);
            }else if($t.parent().find('.swiper-button').length>=1){
                $t.parent().find('.swiper-button-prev').addClass('swiper-button-prev-'+index);
                $t.parent().find('.swiper-button-next').addClass('swiper-button-next-'+index);
            }

            if($t.find('.swiper-slide').length<=1) $('.slider-click[data-pagination-rel="'+$t.data('pagination-rel')+'"]').addClass('disabled');

            var slidesPerViewVar = ($t.data('slides-per-view'))?$t.data('slides-per-view'):1,
                loopVar = ($t.data('loop'))?parseInt($t.data('loop'), 10):0;
            if(slidesPerViewVar!='auto') slidesPerViewVar = parseInt(slidesPerViewVar, 10);

            swipers['swiper-'+index] = new Swiper('.swiper-'+index,{
                // paginationType: ($t.data('pagination'))?$t.data('pagination'):'bullets',
                pagination: '.swiper-pagination-'+index,
                paginationClickable: true,
                nextButton: '.swiper-button-next-'+index,
                prevButton: '.swiper-button-prev-'+index,
                slidesPerView: slidesPerViewVar,
                autoHeight: ($t.data('auto-height'))?parseInt($t.data('auto-height'), 10):0,
                loop: loopVar,
                autoplay: ($t.data('autoplay'))?parseInt($t.data('autoplay'), 10):0,
                centeredSlides: ($t.data('center'))?parseInt($t.data('center'), 10):0,
                breakpoints: ($t.data('breakpoints'))? { 767: { slidesPerView: parseInt($t.attr('data-xs-slides'), 10) }, 991: { slidesPerView: parseInt($t.attr('data-sm-slides'), 10) }, 1199: { slidesPerView: parseInt($t.attr('data-md-slides'), 10) } } : {},
                initialSlide: ($t.data('ini'))?parseInt($t.data('ini'), 10):0,
                watchSlidesProgress: true,
                speed: ($t.data('speed'))?parseInt($t.data('speed'), 10):500,
                parallax: ($t.data('parallax'))?parseInt($t.data('parallax'), 10):0,
                slideToClickedSlide: true,
                keyboardControl: true,
                mousewheelControl: ($t.data('mousewheel'))?parseInt($t.data('mousewheel'), 10):0,
                mousewheelReleaseOnEdges: true,
                spaceBetween: ($t.data('space'))?parseInt($t.data('space'), 10):0,
                direction: ($t.data('direction'))?$t.data('direction'):'horizontal',
                paginationType: ($t.data('pagination'))?$t.data('pagination'):'bullets',
                paginationCustomRender: function(swiper, current, total){
                    return ((current.toString().length<2)?('<span class="swiper-pagination-current">0'+current +'</span>'):current)  + '<span class="line"></span>' + ((total.toString().length<2)?('0'+total):total) ;
                }
                
            });
            swipers['swiper-'+index].update();
            initIterator++;
        });
        $('.swiper-container.swiper-control-top-js').each(function(){
            swipers['swiper-'+$(this).attr('id')].params.control = swipers['swiper-'+$(this).closest('.swipers-couple-wrapper').find('.swiper-control-bottom-js').attr('id')];
        });
        $('.swiper-container.swiper-control-bottom-js').each(function(){
            swipers['swiper-'+$(this).attr('id')].params.control = swipers['swiper-'+$(this).closest('.swipers-couple-wrapper').find('.swiper-control-top-js').attr('id')];
        });

    }


    function watchSwiperProgress(container, swiper, index){
        if($('.homepage-1-backgrounds[data-pagination-rel="'+container.data('pagination-rel')+'"]').length){
            $('.homepage-1-backgrounds .entry.active').removeClass('active');
            $('.homepage-1-backgrounds .entry[data-rel='+index+']').addClass('active');
        }
        if($('.slider-click-label[data-pagination-rel="'+container.data('pagination-rel')+'"]').length){
            $('.slider-click-label[data-pagination-rel="'+container.data('pagination-rel')+'"]').removeClass('active prev next');
            $('.slider-click-label[data-pagination-rel="'+container.data('pagination-rel')+'"][data-slide-to="'+index+'"]').addClass('active');
        }
        if($('.pagination-slider-wrapper[data-pagination-rel="'+container.data('pagination-rel')+'"]').length){
            var foo = $('.pagination-slider-wrapper[data-pagination-rel="'+container.data('pagination-rel')+'"]');
            foo.css({'top':(-1)*parseInt(foo.find('.active').attr('data-slide-to'), 10)*foo.parent().height()});
        }        
    }

    var slide_index = 1;
    $('.all-slides').text($('.left-right .swiper-container.my-bg-swiper .swiper-slide').length);
    $('.prev-slide').text(slide_index);
    $('.next-slide').text(slide_index+1);

    $('.slider-click.left').on('click', function(){
        if($(this)[0].hasAttribute('data-pagination-rel')){
            swipers['swiper-'+$('.swiper-container[data-pagination-rel="'+$(this).data('pagination-rel')+'"]').attr('id')].slidePrev();
            $(this).find('.preview-entry').removeClass('active');
        }
    });

    $('.slider-click.right').on('click', function(){
        if($(this)[0].hasAttribute('data-pagination-rel')){
            swipers['swiper-'+$('.swiper-container[data-pagination-rel="'+$(this).data('pagination-rel')+'"]').attr('id')].slideNext();
            $(this).find('.preview-entry').removeClass('active');
        }
    });

    $('.slider-click-label').on('click', function(){
        swipers['swiper-'+$('.swiper-container[data-pagination-rel="'+$(this).data('pagination-rel')+'"]').attr('id')].slideTo($(this).data('slide-to'));
    });




    /*==============================*/
    /* 08 - buttons, clicks, hovers */
    /*==============================*/

    //open overlay popup
    $('.open-overlay').on('click', function(){
        var $this = $(this);
        $('.overlay[data-rel="'+$(this).data('rel')+'"]').addClass('active');
        if($(this).hasClass('open-video')) setTimeout(function(){$('.overlay[data-rel="'+$this.data('rel')+'"] iframe').attr('src', $this.data('src'));}, 500);
        if(_ismobile) setTimeout(function(){htmlVal.addClass('overflow-hidden');}, 500);
    });

    //close overlay popup
    $('.overlay .button-close').on('click', function(){
        $(this).closest('.video-popup').find('iframe').attr('src', '');
        if($('.overlay.active').length===1) htmlVal.removeClass('overflow-hidden');
        $(this).closest('.overlay').removeClass('active');
    });



    //input animations on focus
    $('.input').on('focus', function(){
        $(this).parent().addClass('focus');
    });

    $('.input').on('blur', function(){
        if($(this).val()==='') $(this).parent().removeClass('focus');
    });



    /*==============================*/
    /* 09 - New */
    /*==============================*/
    var scroll_index = 0;

//sorting-menu click
    $('.sorting-menu .button-drop').on('click', function(){
        var list = $('.sorting-menu ul');
            if($(this).hasClass('active')){
            $(this).removeClass('active');
            list.removeClass('active');
        }else{
            $(this).addClass('active');
            list.addClass('active');
        }
        return false;
    });


   
    /*window scroll*/




//pages scroll (.nav-fix-a; .scroll-animate)

var scrollingAnimate = 0;

$('.nav-fix-a').on('click', function(){
    if(scrollingAnimate) return false;
      scrollingAnimate = 1;
        var index = $(this).parent().find('.nav-fix-a').index(this);
        $('body, html').animate({'scrollTop':$('.scroll-animate').eq(index).offset().top}, function(){scrollingAnimate = 0;});
      $(this).addClass('active').parent().find('.active').not(this).removeClass('active');
      window.location.hash = $(this).attr('data-link');
});

$('.scroll-animate').on('mousewheel', function(event) {
    if(!_isresponsive){
        var thisH = $(this).height(),
            winH = $(window).height(),
        thisTop = $(this).offset().top,
        winScr = $(window).scrollTop();

        if(event.deltaY<0) {
            if(thisH>winH && (thisH+thisTop)>(winH+winScr)){
        
            }
            else{
                if($('.nav-fix-a.active').next().hasClass('nav-fix-a')){
                    event.preventDefault();
                    $('.nav-fix-a.active').next().click();
                }
            
          }
        }
        else {
            if(thisH>winH && (thisTop)<(winScr)){
        
            }
            else{
                event.preventDefault();
                if(thisTop<winScr) $('.nav-fix-a.active').click();
                else $('.nav-fix-a.active').prev().click();
          }
        }
    }     
});

var  stop_out;
       
$.fn.scrollStopped = function(callback) {
    if(!_isresponsive){      
        $(this).scroll(function(){
            var self = this, $this = $(self);
            if ($this.data('scrollTimeout')) {
                stop_out = $this.data('scrollTimeout');
                clearTimeout($this.data('scrollTimeout'));
            }
            $this.data('scrollTimeout', setTimeout(callback,500,self));
        });
    }
};
var index_h_s = 0;

$(window).scrollStopped(function(){
    if(!_isresponsive){
        $('.scroll-animate').each(function(index, element){
            if($(element).offset().top<($(window).scrollTop()+$(window).height()*0.5) && ($(this).height()+$(this).offset().top) > ($(window).scrollTop()+$(window).height()*0.5)){
                if(!$('.nav-fix-a').eq(index).hasClass('active'))$('.nav-fix-a').eq(index).click();
            }
        });
    }
});


    var videoVal = $('.overlay-wrapper.video');

    //overlay hamburger-icon
    $('.hamburger-icon').on('click', function(){
        $('.overlay-wrapper').addClass('active');
        if(videoVal.hasClass('active')){
            videoVal.removeClass('active');
        };
    });

    //overlay video
    $('.btn-play').on('click', function(){
        videoVal.addClass('active');
        var $this = $(this);
        if($(this).hasClass('open-video')) setTimeout(function(){$('iframe').attr('src', $this.attr('data-src'));}, 500);
    });

    //overlay btn-close
    $('.btn-close').on('click', function(){
        $('.overlay-wrapper').removeClass('active');
        var $this = $(this);
        $(this).closest('.overlay-wrapper.video').find('iframe').attr('src', '');
        videoVal.removeClass('active');
    });

    /*excursion-video*/
    $('.excursion-preview img').on( 'click', function() {
        $('.excursion-preview').removeClass('active');
        $(this).closest('.excursion-preview').addClass('active');
        var video_value = $('.excursion-preview.active').attr('data-video-link');
        var img_value = $('.excursion-preview.active').attr('data-img');
        $('.btn-play').attr('data-src', video_value);
        $('.excursion-video img').attr('src', img_value);


    });
    $('.excursion-preview .title').on( 'click', function() {
        $('.excursion-preview').removeClass('active');
        $(this).closest('.excursion-preview').addClass('active');
        var video_value = $('.excursion-preview.active').attr('data-video-link');
        var img_value = $('.excursion-preview.active').attr('data-img');
        $('.btn-play').attr('data-src', video_value);
        $('.excursion-video img').attr('src', img_value);
    });

    
    //overlay plus
   $('.dropdown-plus span').on('click', function(){
        var overmenu_index = $('.dropdown-plus span').index(this);
        if($('.dropdown-plus').eq(overmenu_index).hasClass('active clicked')){
            $('.dropdown-plus').eq(overmenu_index).removeClass('active clicked');
        } else{
            $('.dropdown-plus').eq(overmenu_index).addClass('active clicked'); 
        }
    });

    /*quote-nav click*/
    $('.quote-nav').on('click', function() {
        var quote_index = $('.quote-nav').index(this);
        $('.quote-nav').removeClass('active');
        $(this).addClass('active');
        $(this).closest('.quote').find('article.active').removeClass('active');
        $(this).closest('.quote').find('article').eq(quote_index).addClass('active')
    });


    /*hamburger-icon-2, btn-down*/
    $('.hamburger-icon-2, .btn-down').on('click', function(event){
        event.preventDefault();
        var anchor = $(this).data('anchor');
        $('nav ul li a').parent().removeClass('active');
        $('nav ul li:eq(1)').addClass('active');
        $('html, body').animate({scrollTop:$('#'+anchor).offset().top}, 1000);
    });
    
    
    /*menu click*/
    $('nav ul li a').on('click',function(event){
      if ($(this).attr('data-anchor').length) {
            event.preventDefault();
            var anchor = $(this).data('anchor');
            $('nav ul li a').parent().removeClass('active');
            $(this).parent().addClass('active');
            $('html, body').animate({scrollTop:$('#'+anchor).offset().top}, 1000);
       }
    });

    //hamburger-icon-3
    $('.hamburger-icon-3').on('click', function(){
        if ($(this).hasClass('active')) {
            $(this).removeClass('active');
            headerVal.removeClass('active');
        } else {
                $(this).addClass('active');
                headerVal.addClass('active');
                }
    });


    /*----*/
    /*SHOP*/
    /*----*/
    
    /*SumoSelect*/
    if($('.select-box').length > 0){   
        $('.select-box').SumoSelect();
    };

    /*slider-range*/
    if($('#slider-range').length > 0){
        $( function() {
            $( "#slider-range" ).slider({
              range: true,
              min: 10,
              max: 500,
              values: [ 10, 300 ],
              slide: function( event, ui ) {
                $( "#amount" ).val( "$" + ui.values[ 0 ] + " - $" + ui.values[ 1 ] );
              }
            });
            $( "#amount" ).val( "$" + $( "#slider-range" ).slider( "values", 0 ) +
              " - $" + $( "#slider-range" ).slider( "values", 1 ) );
        });
    };

    /*view-btn*/
    $('.shop .view-btn').on('click', function(){
        $('.view-btn').removeClass('active');
        $(this).addClass('active');
    });

    /*shop-category-menu*/
    $('.category-shop').on('click', function(){
        var toggle_text = $(this).attr('data-text');
        $('.category-toggle span').text(toggle_text);
        $('.category-shop').removeClass('active');
        $(this).addClass('active');
        return false;
    });

    /*category-toggle*/
    $('.category-toggle').on( 'click', function() {
        $(".category").slideToggle(300);
        if($(this).hasClass('active')){
            $(this).removeClass('active');
        } else $(this).addClass('active');
    });


    //open and close popup
    $('.open-popup').on( 'click', function() {
        $('.popup-content').removeClass('active');
        $('.popup-wrapper, .popup-content[data-rel="'+$(this).data('rel')+'"]').addClass('active');
        htmlVal.addClass('overflow-hidden');
        return false;
    });

    $('.popup-wrapper .button-close, .popup-wrapper .layer-close').on( 'click', function() {
        $('.popup-wrapper, .popup-content').removeClass('active');
        htmlVal.removeClass('overflow-hidden');
        setTimeout(function(){
            $('.ajax-popup').remove();
        },300);
        return false;
    });



});