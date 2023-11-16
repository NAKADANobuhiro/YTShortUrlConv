---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

<h1>YouTube ショート動画の URL を通常版に変換</h1>

<script>
function DoConvert()
{
    let ytshorsturl = document.getElementById("ytshorsturl");
    let normalurl = ytshorsturl.value.match(/shorts\/([a-z0-9]+)/i);
    normalurl = 'https://www.youtube.com/watch?v=' + normalurl[1];
    document.getElementById("ytnormalurl").value = normalurl;
};

function DoCopy()
{
    let ytnormalurl = document.getElementById("ytnormalurl").value;
    console.log(ytnormalurl);
    copyToClipboard(ytnormalurl);
};

function copyToClipboard (tagValue) {
  if (navigator.clipboard) {
    return navigator.clipboard.writeText(tagValue).then(function () {})
  } else {
    tagText.select();
    document.execCommand('copy');
  }
}

</script>

## 変換フォーム

<form>
<p>
    <label for="label_shorts_url">YouTube Shorts URL : </label>
    <input type="text" id="ytshorsturl" name="YouTube Shorts URL" value="https://www.youtube.com/shorts/QcDWiB3J1zo?feature=share" size=60 />
    <input type="button"  value="変換" onclick="DoConvert()">
</p>
<p>
    <label for="label_normal_url">YouTube Normal URL : </label>
    <input type="text" id="ytnormalurl" name="YouTube URL" size=60 />
    <input type="button"  value="コピー" onclick="DoCopy()">
</p>
</form>

## 使用方法

YouTube のショート動画は、音量調整ができない、細かな設定ができない、Note.com で埋め込むとインプレース再生されないなどの問題があります。
そこで、ショート動画の共有か、右クリック「動画のURLをコピー」で得た URL を入力すると通常の YouTube で再生される URL を得ることができます。

## ショート動画の再生例

<iframe width="315" height="560" src="https://www.youtube.com/embed/QcDWiB3J1zo" title="YouTubeショートのご紹介" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## 通常版の再生例

<iframe width="560" height="315" src="https://www.youtube.com/embed/QcDWiB3J1zo?si=b14KCUy022_MsbXD" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## 仕組み

仕組みは、YouTube ショート動画の URL から動画の ID を抜き出し、通常の URL で使用されている "https://www.youtube.com/watch?v=" と連結させています。
単純な仕組みですので、本サイトを使用せずにテキストエディターでも修正できます。