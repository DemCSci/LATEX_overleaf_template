**初始模板样式及引用方式**
```
上传zip文件至overleaf（New Project-Upload Project）,得到下图初始模板
```

![image](https://user-images.githubusercontent.com/38340783/114516647-2ec71000-9c70-11eb-810c-4bb1a142b64e.png)



**（1）图占双栏**
```
%样式写法
\begin{figure*}[hb]             %h:放在此处, p:放在本页, t:top, b:bottom  
    \centering  
    \subfigure[XXSubfig1CaptionXX   \label{fig:Subfig1}]                 %XXSubfig1CaptionXX是标题，fig:Subfig1用于引用
    {  
	\begin{minipage}[b]{0.5\linewidth}  
	    \centering  
	    \includegraphics[width=1\linewidth]{picture/xxx.png}  
	\end{minipage}%  
    }%  
    \subfigure[XXSubfig2CaptionXX   \label{fig:Subfig2}]  
    {  
	\begin{minipage}[b]{0.5\linewidth}  
	    \centering  
	    \includegraphics[width=1\linewidth]{picture/xxx.png}  
	\end{minipage}%  
    }%   
    \centering  
    \caption{XXTotalCaptionXX}\label{fig:FigTotal}   %caption标题,label引用  
\end{figure*}  


%文章中引用
Figure~\ref{fig:FigTotal}
```
![image](https://user-images.githubusercontent.com/38340783/114511647-c45fa100-9c6a-11eb-9503-8a007c6859df.png)

**（2）图占单栏**
```
%样式写法
\begin{figure}[!t]                  %t:top, b:bottom  
    \centering  
    \includegraphics[width=0.9\columnwidth]{picture/xxx.png}  
    \caption{XXFigCaptionXX}  
	\label{fig:Fig}            %caption标题,label引用  
\end{figure} 


%文章中引用
Figure~\ref{fig:Fig}
```
![image](https://user-images.githubusercontent.com/38340783/114512246-7b5c1c80-9c6b-11eb-9bdc-9262a319dd04.png)

**（3）表**
```
%样式写法
\renewcommand\arraystretch{1.3}
\begin{table}[!htbp]                  %若双栏此处改成\begin{table*}[hb]
\centering
\setlength{\abovecaptionskip}{0pt}%    
\caption{Simulation Parameters}
\label{tab:Simulation Parameters}
\ 
\newline
\begin{tabular*}{\linewidth}{lll}
\hline
\hline
{\bf Category} & {\bf Parameter} & {\bf Default Value} \\
\hline
Sumo & Scene Information & Munich City, \\ 
  &  & Arrival Rate (1,1.43,2) Veh/s \\
  &  & Single Signal Intersection, \\
  &  & Single Junction (20,40,60) Veh \\
  &  & Bologna City, \\
  &  & Real Traffic Flow in 8:00-9:00 \\
  & Detector Length & (40,50,60,...,140) m \\
  &  & Automatic Adjust, min 40m \\
\hline
Veins & Beacon Rate & 1HZ \\
  & Transmission Power & 20mW \\
\hline
Tracker & Eavesdropper Range & 300m \\
  & Eavesdropper Position & Full Coverage and Overlap 30m \\
  & Track Interval & 1s\\
\hline
\hline
\end{tabular*}
\end{table}                   %若双栏此处改成\end{table*}


%文章中引用
Table \ref{tab:Simulation Parameters}
```
![image](https://user-images.githubusercontent.com/38340783/114513165-7ba8e780-9c6c-11eb-960a-0449db60c2d4.png)

**（4）算法**
```
%样式写法
\begin{algorithm}[!htbp] %算法开始 
\caption{TLAS Simulation Algorithm} %算法的题目 
\label{alg4.1} %算法的标签 
\begin{algorithmic}[1] %此处的[1]控制一下算法中的每句前面都有标号 

\REQUIRE Map status $map$, The current time $t$.
\ENSURE Latest TLAS location information $POS_{SM}$, \\ \quad \quad \ Vehicle silence status status[$vehicle$].
\STATE $I_{SM},POS_{SM}$ = getRSUBeacon($t$)
\FORALL {$vehicles$ $\epsilon$ $map$}
    \IF {getPos($vehicle$) in $POS_{SM}$}
        \IF {$I_{SM}$ == 0}
            \STATE status[$vehicle$] = nosilent
            \STATE $N_{vehicle}$ = setRefreshClock()
            \IF {greenLight in end}
                \STATE totalVehicle = setPredictModel($N_{vehicle}$,greenLight.time())
                \STATE $POS_{SM}$ = setNewLength()
                \STATE setRefreshBeacon()
            \ENDIF
        \ELSE 
            \STATE status[$vehicle$] = silent
            \STATE setSilent(vehicle)
        \ENDIF
    \ENDIF
\ENDFOR 

\end{algorithmic} 
\end{algorithm}


%文章中引用
Algorithm \ref{alg4.1}
```
![image](https://user-images.githubusercontent.com/38340783/114513640-fd991080-9c6c-11eb-9ca5-cf91cd804973.png)


**（5）公式**
```
采用Mathpix Snipping Tool软件。
免费下载地址：https://mathpix.com/
可直接截取公式，转化成对应latex格式，直接粘贴至overleaf即可，$为原行，$$为另起一行。

公式默认为单栏，若是想让公式双栏，可用图片格式包裹，里面不放图片放公式。
```
![image](https://user-images.githubusercontent.com/38340783/114514559-00483580-9c6e-11eb-8742-3203373385b3.png)


**（6）文字高亮更改颜色**
```
%引用包
\usepackage{url}           %该句在含url时自动转化网址格式，可注释
\usepackage{color}
\definecolor{M}{rgb}{0,0,1}  

%样式写法
\textcolor{M}{xxxx}
```
![image](https://user-images.githubusercontent.com/38340783/114515526-07bc0e80-9c6f-11eb-9f4c-45a1a8717757.png)


**（7）主题词替代**
```
%引用包
\usepackage{xspace}
\def\ourshort{{TLAS}\xspace}

%样式写法
\ourshort
```
![image](https://user-images.githubusercontent.com/38340783/114515921-7600d100-9c6f-11eb-813d-d4db36ca567a.png)


**（8）参考文献**
```
谷歌学术中bib内容直接粘贴至.bib文件中即可

%引用方法
\cite{xxx}    %xxx为{与第一个,中间内容
```
![image](https://user-images.githubusercontent.com/38340783/114519916-77cc9380-9c73-11eb-85e0-303d79cd4221.png)



**（9）学术英文参考**
```
https://www.phrasebank.manchester.ac.uk
曼彻斯特大学学术短语银行http://www.phrasebank.manchester.ac.uk/汇集了所有论文需要用到的转接语句引导语句总结语句

```





