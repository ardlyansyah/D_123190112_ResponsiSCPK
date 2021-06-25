### Listing Program :
```
function varargout = responsi(varargin)
% RESPONSI MATLAB code for responsi.fig
%      RESPONSI, by itself, creates a new RESPONSI or raises the existing
%      singleton*.
%
%      H = RESPONSI returns the handle to a new RESPONSI or the handle to
%      the existing singleton*.
%
%      RESPONSI('CALLBACK',hObject,eventData,handles,...) calls the local
%      function named CALLBACK in RESPONSI.M with the given input arguments.
%
%      RESPONSI('Property','Value',...) creates a new RESPONSI or raises the
%      existing singleton*.  Starting from the left, property value pairs are
%      applied to the GUI before responsi_OpeningFcn gets called.  An
%      unrecognized property name or invalid value makes property application
%      stop.  All inputs are passed to responsi_OpeningFcn via varargin.
%
%      *See GUI Options on GUIDE's Tools menu.  Choose "GUI allows only one
%      instance to run (singleton)".
%
% See also: GUIDE, GUIDATA, GUIHANDLES

% Edit the above text to modify the response to help responsi

% Last Modified by GUIDE v2.5 25-Jun-2021 15:12:27

% Begin initialization code - DO NOT EDIT
gui_Singleton = 1;
gui_State = struct('gui_Name',       mfilename, ...
                   'gui_Singleton',  gui_Singleton, ...
                   'gui_OpeningFcn', @responsi_OpeningFcn, ...
                   'gui_OutputFcn',  @responsi_OutputFcn, ...
                   'gui_LayoutFcn',  [] , ...
                   'gui_Callback',   []);
if nargin && ischar(varargin{1})
    gui_State.gui_Callback = str2func(varargin{1});
end

if nargout
    [varargout{1:nargout}] = gui_mainfcn(gui_State, varargin{:});
else
    gui_mainfcn(gui_State, varargin{:});
end
% End initialization code - DO NOT EDIT


% --- Executes just before responsi is made visible.
function responsi_OpeningFcn(hObject, eventdata, handles, varargin)
% This function has no output args, see OutputFcn.
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
% varargin   command line arguments to responsi (see VARARGIN)

% Choose default command line output for responsi
handles.output = hObject;

% Update handles structure
guidata(hObject, handles);

% UIWAIT makes responsi wait for user response (see UIRESUME)
% uiwait(handles.figure1);


% --- Outputs from this function are returned to the command line.
function varargout = responsi_OutputFcn(hObject, eventdata, handles) 
% varargout  cell array for returning output args (see VARARGOUT);
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Get default command line output from handles structure
varargout{1} = handles.output;


% --- Executes on button press in pushbutton1.
function pushbutton1_Callback(hObject, eventdata, handles)
% hObject    handle to pushbutton1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
data = readmatrix('responsi2.xlsx'); %memasukkan data;
data(:,2) = []; %menghapus data kota
data(:,1) = []; %menghapus data no

dataa = readmatrix('responsi2.xlsx'); %memasukkan data;
dataa(:,2) = []; %menghapus data kota

k=[0,1,1,1,1,1]; %membuat nilai atribut
w=[0.3,0.2,0.23,0.1,0.07,0.1]; %memasukkan bobot
%tahapan 1. normalisasi matriks
[m n]=size (data); %matriks m x n dengan ukuran sebanyak variabel data (input)
R=zeros (m,n); %membuat matriks R, yang merupakan matriks kosong
Y=zeros (m,n); %membuat matriks Y, yang merupakan titik kosong
for j=1:n,
    if k(j)==1, %statement untuk kriteria dengan atribut keuntungan
    R(:,j)=data(:,j)./max(data(:,j));
    else
    R(:,j)=min(data(:,j))./data(:,j);%statement untuk kriteria dengan atribut biaya
    end;
end;
for i=1:m,
    V(i)= sum(w.*R(i,:));
end;

data2 = V; %membuat data2 sama dengan vektor V

[o p] = size(data2); %melakukan sorting data
for i = p:-1:1;
    for j = 1:i-1;
        if data2(j)<data2(j+1);
            T = data2(j);
            U = dataa(j);
            data2(j) = data2(j+1);
            dataa(j) = dataa(j+1);
            data2(j+1) = T;
            dataa(j+1) = U;
        end;
    end;
end;
datab = dataa(1:20); %membuat datab berisi data no 
set(handles.uitable2,'data',datab');



% --- Executes on button press in pushbutton2.
function pushbutton2_Callback(hObject, eventdata, handles)
% hObject    handle to pushbutton2 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
close; %menutup program


% --- Executes on button press in pushbutton3.
function pushbutton3_Callback(hObject, eventdata, handles)
% hObject    handle to pushbutton3 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
data = readmatrix('responsi2.xlsx'); %menampilkan data
data(:,2) = [];
set(handles.uitable1,'data',data);

```

### Output Program :
![image](https://user-images.githubusercontent.com/82427614/123428102-a4941400-d5ef-11eb-8a84-4cb8ff629d14.png)
