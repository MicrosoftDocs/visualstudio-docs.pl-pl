---
title: Debugowanie kodu użytkownika przy użyciu tylko mój kod | Dokumentacja firmy Microsoft
ms.date: 02/13/2019
ms.topic: conceptual
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18471a94720a7e625cc183685a83c9f5388c64bb
ms.sourcegitcommit: b623042906de4f12d68af365e36eb38b7b44aa90
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56270618"
---
# <a name="debug-only-user-code-with-just-my-code"></a>Debuguj tylko kod użytkownika przy użyciu tylko mój kod

*Tylko mój kod* jest funkcją debugowania programu Visual Studio automatycznie kroków za pośrednictwem wywołania systemu, framework i inny kod niezwiązany z użytkownikiem. W **stos wywołań** oknie tylko mój kod zwija te wywołania do **[kod zewnętrzny]** ramek.

Tylko mój kod działa inaczej w projektach .NET Framework, C++ i JavaScript.

## <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Włącz lub wyłącz opcję tylko mój kod

Dla większości języków programowania tylko mój kod jest włączona domyślnie.

- Aby włączyć lub wyłączyć opcję tylko mój kod w programie Visual Studio, w obszarze **narzędzia** > **opcje** (lub **debugowania** > **opcje**) > **Debugowanie** > **ogólne**, zaznacz lub odznacz opcję **Włącz tylko mój kod**.

![Włącz opcję tylko mój kod w oknie dialogowym Opcje](../debugger/media/dbg_justmycode_options.png "Włącz tylko mój kod")

> [!NOTE]
> **Włącz opcję tylko mój kod** jest ustawieniem globalnym, która ma zastosowanie do wszystkich projektów programu Visual Studio, we wszystkich językach.

## <a name="just-my-code-debugging"></a>Tylko mój kod, debugowanie

Podczas sesji debugowania **modułów** Pokazuje okno, które kodu debuger jest traktowanie jako mój kod (użytkownika), moduły wraz z ich symboli podczas ładowania stanu. Aby uzyskać więcej informacji, zobacz [zapoznać się z jak dołącza debuger do swojej aplikacji](../debugger/debugger-tips-and-tricks.md#modules_window).

![Kod użytkownika w oknie moduły](../debugger/media/dbg_justmycode_module.png "kod użytkownika w oknie modułów")

W **stos wywołań** lub **zadania** oknie tylko mój kod zwija niebędący kodem użytkownika w ramce kodu z adnotacjami wyszarzona etykietą `[External Code]`.

![Ramka zewnętrzna kod w oknie wywołania stosu](../debugger/media/dbg_justmycode_externalcode.png "ramki kodu zewnętrznego")

>[!TIP]
>Aby otworzyć **modułów**, **stos wywołań**, **zadania**, lub większość innych okien debugowania, musi być w sesji debugowania. Podczas debugowania, w obszarze **debugowania** > **Windows**, wybierz pozycję windows, który chcesz otworzyć.

<a name="BKMK_Override_call_stack_filtering"></a> Aby wyświetlić kod w zwiniętych **[kod zewnętrzny]** ramki, kliknij prawym przyciskiem myszy **stos wywołań** lub **zadań** okna, a następnie wybierz **Pokaż kod zewnętrzny**z menu kontekstowego. Zamień wiersze kodu zewnętrznego rozwiniętej **[kod zewnętrzny**] ramki.

![Pokaż kod zewnętrzny, w oknie wywołania stosu](../debugger/media/dbg_justmycode_showexternalcode.png "Pokaż kod zewnętrzny")

> [!NOTE]
> **Pokaż kod zewnętrzny** jest profilującym użytkownika bieżącego ustawienia mają zastosowanie do wszystkich projektów we wszystkich językach, które są otwierane przez użytkownika.

Klikając dwukrotnie wiersz kodu zewnętrznego rozwinięty w **stos wywołań** okna wyróżnia wywoływania wiersza kodu w kolorze zielonym w kodzie źródłowym. Dla bibliotek DLL lub innych modułów, nie można odnaleźć lub załadować symboli lub źródłowych nie znaleziono strony może być otwarty.

## <a name="BKMK__NET_Framework_Just_My_Code"></a>.NET framework tylko mój kod

W projektach .NET Framework tylko mój kod używa symbol (*.pdb*) plików i optymalizacje program do klasyfikowania kod użytkownika i niezwiązanych z użytkownikiem. Debuger .NET Framework uwzględnia zoptymalizowane pliki binarne, a nie są ładowane *.pdb* pliki za kod niezwiązany z użytkownikiem.

Trzy atrybuty kompilatora wpływa również na debugera platformy .NET traktuje jako kodu użytkownika:

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> Nakazuje debugerowi, że kod, który jest stosowany do nie jest kodem użytkownika.
- <xref:System.Diagnostics.DebuggerHiddenAttribute> Ukrywa kodu z debugerem, nawet wtedy, gdy tylko mój kod jest wyłączona.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> Nakazuje debugerowi, aby przejść przez kod, który zostanie zastosowany do, a nie kod krok po kroku.

Debuger .NET Framework uwzględnia cały kod jako kodu użytkownika.

Podczas debugowania środowiska .NET Framework:

- **Debugowanie** > **Step Into** (lub **F11**) na temat kroków kod niezwiązany z użytkownikiem za pośrednictwem kodu do następnego wiersza kodu użytkownika.
- **Debugowanie** > **Step Out** (lub **Shift**+**F11**) na niebędący kodem użytkownika działa do następnego wiersza kodu użytkownika.

W przypadku braku więcej kodu użytkownika profilowanie będzie kontynuowane, dopóki kończy się, liczba trafień kolejny punkt przerwania lub zgłasza błąd.

<a name="BKMK_NET_Breakpoint_behavior"></a> Jeśli debuger przerwie działanie na kodzie niezwiązanych z użytkownikiem (na przykład użyć **debugowania** > **Przerwij wszystko** i wstrzymywanie działania, w kodzie niezwiązanych z użytkownikiem), **Brak źródła** zostanie wyświetlone okno. Następnie można użyć **debugowania** > **kroku** polecenie, aby przejść do następnego wiersza kodu użytkownika.

Jeśli wystąpi nieobsługiwany wyjątek w kodzie niezwiązanych z użytkownikiem, debuger przerywa w wierszu kodu użytkownika, gdy wyjątek został wygenerowany.

Włączenie wyjątku pierwszej szansy wyjątki wywołujący wiersz kodu użytkownika jest wyróżniona na zielono w kodzie źródłowym. **Stos wywołań** adnotowanej ramki etykietą jest wyświetlana w oknie **[kod zewnętrzny]**.

## <a name="BKMK_C___Just_My_Code"></a> Tylko mój kod w języku C++
  
Począwszy od programu Visual Studio 2017 w wersji 15.8, tylko mój kod dla kodu przechodzenie krok po kroku jest również obsługiwany. Ta funkcja wymaga również użycia [/JMC (tylko mój kod debugowanie)](/cpp/build/reference/jmc) przełącznika kompilatora. Przełącznik jest domyślnie włączona. Aby uzyskać **stos wywołań** okna i wywołanie stosu pomocy technicznej w tylko mój kod, opcja /JMC nie jest wymagana.

<a name="BKMK_CPP_User_and_non_user_code"></a> Jest uważany za kod użytkownika, plik PDB dla pliku binarnego zawierającego kod użytkownika muszą być ładowane przez debuger (Użyj **modułów** okna, aby to sprawdzić).

Dla zachowania stosu wywołań, tak jak w **stos wywołań** oknie tylko mój kod w języku C++ traktuje tylko te funkcje, aby być *niebędący kodem użytkownika*:

- Funkcje za pomocą informacji o źródle pozbawionego włókien w pliku symboli.
- Funkcje, w której pliki symboli oznacza, że brak pliku źródłowego, odpowiadający ramki stosu.
- Określona w funkcji  *\*.natjmc* pliki *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* folderu.
  
Kod zachowania przechodzenia krok po kroku, tylko mój kod w języku C++ traktuje tylko te funkcje, aby być *niebędący kodem użytkownika*:
  
- Funkcje, dla których odpowiedni plik PDB nie został załadowany w debugerze.
- Określona w funkcji  *\*.natjmc* pliki *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* folderu.

> [!NOTE]
> Obsługę kodu przechodzenia krok po kroku w tylko mój kod, kodu w języku C++ muszą być skompilowane z za pomocą kompilatorów MSVC w programie Visual Studio 15.8 w wersji zapoznawczej 3 lub nowszym oraz przełącznika kompilatora /JMC musi być włączona (jest włączony domyślnie). Aby uzyskać więcej informacji, zobacz [Dostosowywanie C++ stos wywołań i kodem zachowanie przechodzenia krok po kroku](#BKMK_CPP_Customize_call_stack_behavior)) to [wpis w blogu](https://blogs.msdn.microsoft.com/vcblog/2018/06/29/announcing-jmc-stepping-in-visual-studio/). Dla kodu skompilowane przy użyciu starszego kompilatora *.natstepfilter* pliki są jedynym sposobem, aby dostosować program code przechodzenie krok po kroku, który jest niezależny od tylko mój kod. Zobacz [zachowania przechodzenia krok po kroku Dostosowywanie C++](#BKMK_CPP_Customize_stepping_behavior).

<a name="BKMK_CPP_Stepping_behavior"></a> Podczas debugowania języka C++:

- **Debugowanie** > **Step Into** (lub **F11**) na temat kroków kod niezwiązany z użytkownikiem za pośrednictwem kodu do następnego wiersza kodu użytkownika.
- **Debugowanie** > **Step Out** (lub **Shift**+**F11**) na niebędący kodem użytkownika działa do następnego wiersza kodu użytkownika.

W przypadku braku więcej kodu użytkownika profilowanie będzie kontynuowane, dopóki kończy się, liczba trafień kolejny punkt przerwania lub zgłasza błąd.

Jeśli debuger przerwie działanie na kodzie niezwiązanych z użytkownikiem (na przykład użyć **debugowania** > **Przerwij wszystko** i oraz ich wstrzymywania w kodzie niezwiązanych z użytkownikiem), wykonywanie krokowe odbywa się w kod niezwiązany z użytkownikiem.

Jeśli debuger uderza w wyjątku, zatrzymuje na wyjątek, czy jest ono w kodzie użytkownika lub niezwiązanych z użytkownikiem. **Nieobsługiwane przez użytkownika** opcji na liście **ustawienia wyjątków** okno dialogowe, są ignorowane.   
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a> Dostosowywanie C++ stos wywołań i kodu, przechodzenie krok po kroku zachowanie  

Dla projektów języka C++, można określić moduły, pliki źródłowe i funkcji **stos wywołań** okna traktuje jako kod niezwiązany z użytkownikiem, określając je w  *\*.natjmc* plików. To dostosowanie ma zastosowanie również do kodu, przechodzenie krok po kroku, korzystając z najnowszą wersję kompilatora (zobacz [C++ tylko mój kod](#BKMK_CPP_User_and_non_user_code)).
  
- Aby określić kod niezwiązany z użytkownikiem dla wszystkich użytkowników komputera programu Visual Studio, należy dodać *.natjmc* plik *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* folderu.  
- Aby określić kod niezwiązany z użytkownikiem dla poszczególnych użytkowników, dodać *.natjmc* plik *%USERPROFILE%\My 2017\Visualizers Documents\Visual Studio* folderu.  

A *.natjmc* plik jest plikiem XML o następującej składni:  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">  
  
  <!-- Modules -->  
  <Module Name="ModuleSpec" />  
  <Module Name="ModuleSpec" Company="CompanyName" />  
  
  <!-- Files -->  
  <File Name="FileSpec"/>  
  
  <!-- Functions -->  
  <Function Name="FunctionSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />  
  
</NonUserCode>  
  
```  

 **Atrybuty elementu modułów**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagana. Pełna ścieżka moduł lub moduły. Można używać symboli wieloznacznych Windows `?` (zero lub jeden znak) i `*` (zero lub więcej znaków). Na przykład<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> Nakazuje debugerowi Traktuj wszystkie moduły w *\3rdParty\UtilLibs* na dowolnym dysku jako kodu zewnętrznego.|  
|`Company`|Opcjonalna. Nazwa firmy, która publikuje moduł, który jest osadzony w pliku wykonywalnym. Ten atrybut służy do odróżniania modułów.|  
  
 **Atrybuty elementu pliku**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagana. Pełna ścieżka pliku źródłowego lub pliki, które mają być traktowane jako kodu zewnętrznego. Można używać symboli wieloznacznych Windows `?` i `*` określając ścieżkę.|  
  
 **Atrybuty elementów — funkcja**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagana. W pełni kwalifikowaną nazwę funkcji, które mają być traktowane jako kodu zewnętrznego.|  
|`Module`|Opcjonalna. Nazwa lub pełną ścieżkę do modułu, która zawiera funkcję. Ten atrybut służy do odróżniania funkcji o tej samej nazwie.|  
|`ExceptionImplementation`|Po ustawieniu `true`, stos wywołań Wyświetla funkcja, która zgłosiła wyjątek, a nie z tej funkcji.|  

###  <a name="BKMK_CPP_Customize_stepping_behavior"></a> Dostosowywanie zachowania przechodzenia krok po kroku C++ niezależne od ustawień tylko mój kod

W projektach C++ można określić funkcji, aby przejść przez wymienienie ich jako kod niezwiązany z użytkownikiem w  *\*.natstepfilter* plików. Funkcje wymienione w  *\*.natstepfilter* pliki nie są zależne od ustawień tylko mój kod.
  
- Aby określić kod niezwiązany z użytkownikiem dla wszystkich użytkowników lokalnych z programu Visual Studio, należy dodać *.natstepfilter* plik *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* folderu.  
- Aby określić kod niezwiązany z użytkownikiem dla poszczególnych użytkowników, dodać *.natstepfilter* plik *%USERPROFILE%\My 2017\Visualizers Documents\Visual Studio* folderu.  
  
A *.natstepfilter* plik jest plikiem XML o następującej składni:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Action>StepAction</Action>  
    </Function>  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Module>ModuleSpec</Module>  
        <Action>StepAction</Action>  
    </Function>  
</StepFilter>  
  
```  
  
|Element|Opis|  
|-------------|-----------------|  
|`Function`|Wymagana. Określa jedną lub więcej funkcji jako funkcje niezwiązanych z użytkownikiem.|  
|`Name`|Wymagana. ECMA 262 sformatowane wyrażeń regularnych, określając nazwę pełne działanie do dopasowania. Na przykład:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> Nakazuje debugerowi, że wszystkie metody w `MyNS::MyClass` należy uznać za kod niezwiązany z użytkownikiem. W dopasowaniu jest uwzględniana wielkość liter.|  
|`Module`|Opcjonalna. ECMA 262 sformatowane wyrażeń regularnych, określić pełną ścieżkę do modułu zawierający funkcję. Dopasowanie jest rozróżniana wielkość liter.|  
|`Action`|Wymagana. Jedną z następujących wartości rozróżniana wielkość liter:<br /><br /> `NoStepInto`  -Nakazuje debugerowi na wkroczenie za pośrednictwem funkcji.<br /> `StepInto`  -Nakazuje debugerowi na wkroczenie do funkcji zastąpienie wszelkich innych `NoStepInto` dopasowane funkcji.| 
  
##  <a name="BKMK_JavaScript_Just_My_Code"></a> Tylko mój kod języka JavaScript  

<a name="BKMK_JS_User_and_non_user_code"></a> JavaScript tylko mój kod kontrolki przechodzenie krok po kroku, a następnie wywołać wyświetlanie stosu przez skategoryzowanie kodu w jednym z tych klasyfikacji:  

|||  
|-|-|  
|**MyCode**|Kod użytkownika, który umożliwia zbieranie i kontrolowanie.|  
|**LibraryCode**|Kod niezwiązany z użytkownikiem z bibliotek, które regularnie używane i aplikacji zależy od działał poprawnie (na przykład WinJS lub jQuery).|  
|**UnrelatedCode**|Kod niezwiązany z użytkownikiem w aplikację, która nie jest własnością i aplikacja nie jest zależny od działał poprawnie. Na przykład advertising SDK, który wyświetla reklamy, może być UnrelatedCode. W projektach platformy uniwersalnej systemu Windows każdy kod, który jest ładowany do aplikacji za pomocą protokołu HTTP lub HTTPS identyfikatora URI jest również uważana za UnrelatedCode.|  

Debuger JavaScript klasyfikuje kod jako użytkownika lub niezwiązanych z użytkownikiem w następującej kolejności:  
  
1. Domyślne klasyfikacje.  
   -   Skrypt wykonywany, przekazując ciąg do hosta — pod warunkiem `eval` funkcja **MyCode**.  
   -   Skrypt wykonywany, przekazując ciąg do `Function` Konstruktor jest **LibraryCode**.  
   -   Skrypt w odwołaniu do struktury, takich jak WinJS lub zestawu Azure SDK jest **LibraryCode**.  
   -   Skrypt wykonywany, przekazując ciąg do `setTimeout`, `setImmediate`, lub `setInterval` funkcje **UnrelatedCode**.  
   
2. Klasyfikacje, określony dla wszystkich projektów Visual Studio JavaScript w *%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json* pliku.  
   
3. Klasyfikacje w *mycode.json* pliku bieżącego projektu.  
  
Każdy krok klasyfikacji zastąpienia poprzednich kroków. 

Inny kod jest klasyfikowana jako **MyCode**.  

Możesz zmodyfikować domyślne klasyfikacje i klasyfikowania określonych plików i adresy URL jako kod użytkownika lub niezwiązanych z użytkownikiem, dodając *.json* plik o nazwie *mycode.json* do głównego folderu projektu w języku JavaScript. Zobacz [dostosować tylko mój kod JavaScript](#BKMK_JS_Customize_Just_My_Code). 

<a name="BKMK_JS_Stepping_behavior"></a> Podczas debugowania języka JavaScript:

- Jeśli funkcja znajduje się kod niebędący użytkownikiem **debugowania** > **Step Into** (lub **F11**) działa tak samo jak **debugowania**  >  **Przekrocz** (lub **F10**).
- Jeśli krok rozpoczyna się w niezwiązanych z użytkownikiem (**LibraryCode** lub **UnrelatedCode**) kodu, przechodzenie krok po kroku tymczasowo zachowuje się tak, jakby nie włączono opcję tylko mój kod. Gdy krok do kodu użytkownika, tylko mój kod przechodzenie krok po kroku zostanie ponownie włączony.
- Gdy użytkownik wyniki kroku kodu w opuszczania bieżącego kontekstu wykonywania, debuger zatrzymuje się w następnym wierszu kodu użytkownika wykonane. Na przykład, jeśli wykonuje wywołanie zwrotne **LibraryCode** kod, Debuger kontynuuje do czasu następnego wiersza kodu użytkownika jest wykonywana.
- **Step Out** (lub **Shift**+**F11**) zatrzymuje się w następnym wierszu kodu użytkownika.

W przypadku braku więcej kodu użytkownika profilowanie będzie kontynuowane, dopóki kończy się, liczba trafień kolejny punkt przerwania lub zgłasza błąd.

Punkty przerwania ustawione w kodzie zawsze są osiągane, ale jest klasyfikowana przez kod.

- Jeśli `debugger` — słowo kluczowe występuje w **LibraryCode**, debuger zawsze przerywa pracę.
- Jeśli `debugger` — słowo kluczowe występuje w **UnrelatedCode**, debuger nie zatrzymuje.

<a name="BKMK_JS_Exception_behavior"></a> Jeśli wystąpi nieobsługiwany wyjątek w **MyCode** lub **LibraryCode** kod, debuger zawsze przerywa pracę.

Jeśli wystąpi nieobsługiwany wyjątek w **UnrelatedCode**, i **MyCode** lub **LibraryCode** znajduje się na stos wywołań, podziały debugera.

Jeśli są włączone wyjątki pierwszej szansy, dla wyjątku, a wyjątek występuje w **LibraryCode** lub **UnrelatedCode**:

- Jeśli wyjątek jest obsługiwany, debuger nie zostanie przerwane.
- Jeśli wyjątek nie jest obsługiwany, debuger przerywa.

### <a name="BKMK_JS_Customize_Just_My_Code"></a> Dostosowywanie JavaScript tylko mój kod

Kategoryzowanie, użytkownika i kod niezwiązany z użytkownikiem dla jednego projektu w języku JavaScript, można dodać *.json* plik o nazwie *mycode.json* do folderu głównego projektu.

Specyfikacje w tym pliku przesłonić domyślne klasyfikacje i *mycode.default.wwa.json* pliku. *Mycode.json* pliku nie konieczne utworzenie listy wszystkich pary klucz-wartość. **MyCode**, **bibliotek**, i **Unrelated** wartości mogą być puste tablic.

*Mycode.JSON* plików należy użyć następującej składni:

```json
{
    "Eval" : "Classification",
    "Function" : "Classification",
    "ScriptBlock" : "Classification",
    "MyCode" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ],
    "Libraries" : [
        "UrlOrFileSpec",
        . .
        "UrlOrFileSpec"
    ],
    "Unrelated" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ]
}

```

**Eval, funkcja i ScriptBlock**

**Eval**, **funkcja**, i **ScriptBlock** pary klucz-wartość jak dynamicznie określać jest klasyfikowany wygenerowanego kodu:

|||
|-|-|
|**Eval**|Skrypt, który jest wykonywany, przekazując ciąg do hosta — pod warunkiem `eval` funkcji. Domyślnie skrypt — wersja próbna zostanie sklasyfikowany jako **MyCode**.|
|**Function**|Skrypt, który jest wykonywany, przekazując ciąg do `Function` konstruktora. Domyślnie funkcja skryptu zostanie sklasyfikowany jako **LibraryCode**.|
|**ScriptBlock**|Skrypt, który jest wykonywany, przekazując ciąg do `setTimeout`, `setImmediate`, lub `setInterval` funkcji. Domyślnie skryptów w blok skryptu zostanie sklasyfikowany jako **UnrelatedCode**.|

Możesz zmienić wartość, do jednego z tych słów kluczowych:

- `MyCode` klasyfikuje skryptu jako **MyCode**.
- `Library` klasyfikuje skryptu jako **LibraryCode**.
- `Unrelated` klasyfikuje skryptu jako **UnrelatedCode**.

**MyCode, biblioteki i niepowiązanych**

**MyCode**, **bibliotek**, i **Unrelated** pary klucz-wartość Określ adresy URL lub pliki, które mają zostać uwzględnione w klasyfikacji:

|||
|-|-|
|**MyCode**|Tablicę adresów URL lub pliki, które są klasyfikowane jako **MyCode**.|
|**Biblioteki**|Tablicę adresów URL lub pliki, które są klasyfikowane jako **LibraryCode**.|
|**Niepowiązane**|Tablicę adresów URL lub pliki, które są klasyfikowane jako **UnrelatedCode**.|

Ciąg adresu URL lub pliku może mieć jedną lub więcej `*` znaków, które dopasowuje zero lub więcej znaków. `*` jest taka sama jak wyrażenia regularnego `.*`.
