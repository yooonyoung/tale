---

layout: post

title: "bigfoot.js를 활용한 각주 기능 테스트"

---

bigfoot을 이용하여 각주를 예쁘게 만들고 있다.[^1] 이렇게 하면 된다는데?<sup id="fnref:1"><a href="#fn:1" class="footnote">1</a></sup> 

이게 된다면 본문으로 돌아가는 기능을 위해 또 수정해야 한다.<sup id="fnref:2"><a href="#fn:2" class="footnote">2</a></sup></p>

```
<script type="text/javascript" src="/js/jquery-3.3.1.js"></script>
<script type="text/javascript" src="/js/bigfoot.min.js"></script>
<script src="http://code.jquery.com/jquery-1.10.2.js"></script>
<script type="text/javascript">
        var bigfoot = $.bigfoot(
                       {
                       actionOriginalFN: "ignore",
                       positionContent: "true"
                       }
        );
</script>
```

말을꼭 써야하나?[^eng]

[^1]: 아이디는안써?
[^eng]: 이거야?


<div class="footnotes">
  <ol>
    <li id="fn:1">
      <p>팝오버 창은 이렇게 작동한다. 누르기 편하고 마음에 든다. :)&nbsp;<a href="#fnref:1" class="reversefootnote">&#8617;</a></p>
    </li>
    <li id="fn:2">
      <p>나는 _scss 폴더에 넣어서 import 하는 방식이 잘 적용되지 않아서 이렇게 했다. 어쨌든 제대로 작동한다.&nbsp;<a href="#fnref:2" class="reversefootnote">&#8617;</a></p>
    </li>
  </ol>
</div>