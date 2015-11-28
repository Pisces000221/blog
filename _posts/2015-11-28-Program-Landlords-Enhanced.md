---
layout: post
category : Program
tagline: ""
tags : [Program]
shortContent: "Landlords Enhanced [UOJ]"
---
{% include JB/setup %}

{% highlight C %}

var n,x,i,ans,t:longint;
a,b,c:array[0..15] of longint;

procedure pd(x:longint);
var i,j:longint;
begin
	if x>=ans then exit;
	if x+b[1]+b[2]+b[3]+b[4]<ans then ans:=x+b[1]+b[2]+b[3]+b[4];
	if b[4]>0 then begin
		dec(b[4]);
		for i:=2 to 4 do if b[i]>0 then begin
			dec(b[i]);inc(b[i-2]);
			for j:=2 to 4 do if b[j]>0 then begin
				dec(b[j]);inc(b[j-2]);
				pd(x+1);
				inc(b[j]);dec(b[j-2]);
			end;
			inc(b[i]);dec(b[i-2]);
		end;
		for i:=1 to 4 do if b[i]>0 then begin
			dec(b[i]);inc(b[i-1]);
			for j:=1 to 4 do if b[j]>0 then begin
				dec(b[j]);inc(b[j-1]);
				pd(x+1);
				inc(b[j]);dec(b[j-1]);
			end;
			inc(b[i]);dec(b[i-1]);
		end;
		inc(b[1]);
		for i:=2 to 4 do if b[i]>0 then begin
			dec(b[i]);inc(b[i-2]);
			pd(x+1);
			inc(b[i]);dec(b[i-2]);
		end;
		for i:=1 to 4 do if b[i]>0 then begin
			dec(b[i]);inc(b[i-1]);
			pd(x+1);
			inc(b[i]);dec(b[i-1]);
		end;
		dec(b[1]);inc(b[4]);
	end;
	if b[3]>0 then begin
		dec(b[3]);
		for i:=2 to 4 do if b[i]>0 then begin
			dec(b[i]);inc(b[i-2]);
			pd(x+1);
			inc(b[i]);dec(b[i-2]);
		end;
		for i:=1 to 4 do if b[i]>0 then begin
			dec(b[i]);inc(b[i-1]);
			pd(x+1);
			inc(b[i]);dec(b[i-1]);
		end;
		inc(b[3]);
	end;
end;

procedure dfs(x:longint);
var	i,j,k,l:longint;
begin
	if x>=ans then exit;
	for i:=2 to 12 do if a[i]>=3 then begin
		j:=i;
		while a[j+1]>=3 do inc(j);
		if j-i+1>=2 then begin
			dec(a[i],3);
			for k:=i+1 to j do begin
				dec(a[k],3);dfs(x+1);
			end;
			for k:=i to j do inc(a[k],3);
		end;
	end;
	for i:=2 to 11 do if a[i]>=2 then begin
		j:=i;
		while a[j+1]>=2 do inc(j);
		if j-i+1>=3 then begin
			dec(a[i],2);dec(a[i+1],2);
			for k:=i+2 to j do begin
				dec(a[k],2);dfs(x+1);
			end;
			for k:=i to j do inc(a[k],2);
		end;
	end;
	for i:=2 to 9 do if a[i]>=1 then begin
		j:=i;
		while a[j+1]>=1 do inc(j);
		if j-i+1>=5 then begin
			dec(a[i]);dec(a[i+1]);dec(a[i+2]);dec(a[i+3]);
			for k:=i+4 to j do begin
				dec(a[k]);dfs(x+1);
			end;
			for k:=i to j do inc(a[k]);
		end;
	end;
	l:=0;
	fillchar(b,sizeof(b),0);
	for i:=1 to 13 do inc(b[a[i]]);
	if a[0]=2 then inc(b[1],2);
	if a[0]=1 then inc(b[1]);
	pd(x);
end;

begin
	readln(t,n);
	while t>0 do begin
		dec(t);
		fillchar(a,sizeof(a),0);
		for i:=1 to n do begin
			read(x);
			if x=1 then x:=13 else
			if x<>0 then dec(x);inc(c[x]);
			inc(a[x]);readln(x);
		end; 
		ans:=n;
		dfs(0);
		if a[0]=2 then begin
			a[0]:=0;dfs(1);
		end;
	writeln(ans);
	end;
end.

{% endhighlight %}
