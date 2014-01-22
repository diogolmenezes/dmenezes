---
layout: page
title: "Online GUID Generator"
comments: false
sharing: false
footer: true
---

<script type="text/javascript">
    function GetGuid() {
        var result='';
        for(var i=0; i<32; i++)
            result += Math.floor(Math.random()*16).toString(16).toUpperCase();
        return result
    }

    $(function(){
        $('#guid').html(GetGuid());
        $('#refresh').click(function() {
            $('#guid').html(GetGuid());
        });
    });
</script>

<h2 id="guid"></h2>
<a href="javascript:void(0);" id="refresh">Refresh</a>