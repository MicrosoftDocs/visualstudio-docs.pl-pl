---
title: Tylko mój kod | Dokumenty firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efcabf9c7dc201f95515cd24bf3a14727f7149fe
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302498"
---
# <a name="just-my-code"></a>Tylko mój kod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Deweloperzy, którzy używają języków .NET Framework są zaznajomieni z funkcji debugera Tylko mój kod, który kroki przez system, struktury i innych wywołań innych niż użytkownik i zwija te wywołania w oknach stosu wywołań. Tylko mój kod został rozszerzony na języki C++ i JavaScript. W tym temacie opisano specyfikę używania tylko mojego kodu w programach .NET Framework, natywnych projektach języka C++ i JavaScript.  
  
## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a>Włączanie lub wyłączanie tylko mojego kodu  
 Aby włączyć lub wyłączyć opcję Tylko mój kod, wybierz polecenie **Opcje i ustawienia** w menu **debugowania.** W węźle **Debugowanie** / **ogólne** wybierz lub **wyczyść pozycję Włącz tylko mój kod**.  
  
 ![Włącz tylko mój kod w oknie dialogowym Opcje](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
> Ustawienie **Włącz tylko mój kod** jest ustawieniem globalnym, które jest stosowane do wszystkich projektów programu Visual Studio we wszystkich językach.  
  
### <a name="override-call-stack-filtering"></a><a name="BKMK_Override_call_stack_filtering"></a>Zastępowanie filtrowania stosu wywołań  
 W stosie wywołań wyświetla, takich jak stos wywołań i zadania okna, Tylko mój `[External Code]`kod zwija kod niebędący użytkownikiem do ramki z adnotacjami oznaczone . Aby wyświetlić zwinięte ramki, wybierz polecenie **Pokaż kod zewnętrzny** w menu kontekstowym wyświetlania stosu wywołań.  
  
> [!NOTE]
> Ustawienie **Pokaż kod zewnętrzny** jest zapisywane w profilu bieżącego użytkownika. Jest on stosowany do wszystkich projektów we wszystkich językach, które są otwierane przez użytkownika.  
  
## <a name="net-framework-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>.NET Framework tylko mój kod  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_NET_User_and_non_user_code"></a>Kod użytkownika i osoby niebędące użytkownikiem  
 Aby odróżnić kod użytkownika od kodu niebędącego użytkownikiem, just my code analizuje pliki symboli (pdb) i optymalizacje programów. Debuger uważa, że kod jest kodem niebędącym użytkownikiem, gdy plik binarny jest zoptymalizowany lub gdy plik .pdb nie jest dostępny.  
  
 Trzy atrybuty mają również wpływ na to, co debuger uważa za Mój kod:  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute>informuje debugera, że kod, do który jest stosowany, nie jest my code.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute>ukrywa kod z debugera, nawet jeśli tylko mój kod jest wyłączony.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute>informuje debugera, aby przejść przez kod, który jest stosowany do, a nie krok do kodu.  
  
  Cały inny kod jest uważany za kod użytkownika.  
  
### <a name="stepping-behavior"></a><a name="BKMK_NET_Stepping_behavior"></a>Zachowanie krokowe  
 Po **wejściu do** (skrót klawiaturowy: F11) kod niebędący użytkownikiem, debuger kroki nad kodem do następnej instrukcji użytkownika. Po **wyjęciu** (Klawiatura: Shift + F11), debuger uruchamia się do następnego wiersza kodu użytkownika. Jeśli nie napotkany kod użytkownika następnie wykonanie jest kontynuowane do momentu zakończenia aplikacji, punkt przerwania zostanie trafiony lub występuje wyjątek.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_NET_Breakpoint_behavior"></a>Zachowanie punktu przerwania  
 Gdy opcja Tylko mój kod jest włączona, możesz wybrać **opcję Przerwij wszystko** (klawiatura: Ctrl + Alt + Break) i zatrzymać wykonywanie w miejscu, w którym nie ma kodu użytkownika do wyświetlenia. W takim przypadku zostanie wyświetlone okno Brak źródła. Jeśli następnie wybierzesz step polecenia, debuger przeniesie Cię do następnego wiersza kodu użytkownika.  
  
### <a name="exception-behavior"></a><a name="BKMK_NET_Exception_behavior"></a>Zachowanie wyjątku  
 Jeśli nieobsługiwał wyjątek występuje w kodzie niebędącym użytkownikiem, debuger dzieli się w wierszu w kodzie użytkownika, w którym został wygenerowany wyjątek.  
  
 Jeśli wyjątki pierwszej szansy są włączone dla wyjątku, wiersz kodu użytkownika jest wyróżniony na zielono. Stos wywołań wyświetla ramkę z adnotacjami z etykietą **[Kod zewnętrzny].**  
  
## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a>C++ Tylko mój kod  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_CPP_User_and_non_user_code"></a>Kod użytkownika i osoby niebędące użytkownikiem  
 C++ Just My Code różni się od .NET Framework i JavaScript Just My Code, ponieważ zachowanie stepping jest niezależne od zachowania stosu wywołań.  
  
 **Stosy połączeń**  
  
 Domyślnie debuger uważa te funkcje za kod niebędący użytkownikiem w oknach stosu wywołań:  
  
- Funkcje z usuniętymi informacjami źródłowymi w pliku symboli.  
  
- Funkcje, w których pliki symboli wskazują, że nie ma pliku źródłowego odpowiadającego ramce stosu.  
  
- Funkcje `*.natjmc` określone w `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` plikach w folderze.  
  
  **Stepping**  
  
  Domyślnie tylko funkcje `*.natstepfilter` określone `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` w plikach w folderze są uważane za kod niebędący użytkownikiem.  
  
  Można utworzyć własne `.natstepfilter` `.natjmc` i dostosować zachowanie okna stosu krokowego i wywołania w pliku `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`.  
  
### <a name="stepping-behavior"></a><a name="BKMK_CPP_Stepping_behavior"></a>Zachowanie krokowe  
 Po **wejściu do** (skrót klawiaturowy: F11) kod niebędący użytkownikiem z kodu użytkownika, debuger kroki nad kodem do następnego wiersza kodu użytkownika. Po **wyjęciu** (Klawiatura: Shift + F11), debuger uruchamia się do następnego wiersza kodu użytkownika. Jeśli nie napotkany kod użytkownika następnie wykonanie jest kontynuowane do momentu zakończenia aplikacji, punkt przerwania zostanie trafiony lub występuje wyjątek.  
  
 Jeśli debuger przerwy w kodzie użytkownika (na przykład, jeśli break all polecenie zatrzymuje się w kodzie użytkownika), stepping kontynuuje w kodzie nie-użytkownik.  
  
### <a name="exception-behavior"></a><a name="BKMK_CPP_Exception_behavior"></a>Zachowanie wyjątku  
 Gdy debuger trafi wyjątek, zatrzyma się na wyjątek, niezależnie od tego, czy jest w kodzie użytkownika lub nie-użytkownika. Opcje **nieobsługiwalne przez użytkownika** w oknie dialogowym **Wyjątki** są ignorowane.  
  
### <a name="customize-stepping-behavior"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a>Dostosowywanie zachowania krokkowe  
 Można określić funkcje, które mają być przekroczeniu, wymieniając je jako kod niebędący użytkownikiem w `*.natstepfilter` plikach.  
  
- Aby określić kod niebędący użytkownikiem dla wszystkich użytkowników komputera programu Visual Studio, dodaj plik .natstepfilter do folderu. `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`  
  
- Aby określić kod niebędący użytkownikiem dla pojedynczego użytkownika, dodaj `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` plik .natstepfilter do folderu.  
  
  Pliki .natstepfilter są plikami xml o tej składni:  
  
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
|Funkcja|Wymagany. Określa jedną lub więcej funkcji jako funkcji niebędących użytkownikami.|  
|`Name`|Wymagany. Sformatowane wyrażenie regularne ECMA-262 określające pełną nazwę funkcji do dopasowania. Przykład:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> informuje debugera, że `MyNS::MyClass` wszystkie metody w są uważane za kod niebędący użytkownikiem. W dopasowanie jest rozróżniana wielkość liter.|  
|`Module`|Element opcjonalny. W formacie ECMA-262 wyrażenie regularne określające pełną ścieżkę do modułu zawierającego funkcję. Dopasowanie jest niewrażliwe na argumenty.|  
|`Action`|Wymagany. Jedna z następujących wartości rozróżnianych wielkości liter:<br /><br /> -   `NoStepInto`– informuje debuger, aby przejść przez dopasowana funkcja.<br />-   `StepInto`– informuje debuger, aby wkroczył do dopasowanych `NoStepInto` funkcji, zastępując inne dla dopasowanych funkcji.|  
  
### <a name="customize-call-stack-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a>Dostosowywanie zachowania stosu połączeń  
 Można określić moduły, pliki źródłowe i funkcje, które będą traktowane jako `*.natjmc` kod niebędący użytkownikiem w stosach wywołań, określając je w plikach.  
  
- Aby określić kod niebędący użytkownikiem dla wszystkich użytkowników komputera programu Visual `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` Studio, dodaj plik natjmc do folderu.  
  
- Aby określić kod niebędący użytkownikiem dla pojedynczego użytkownika, `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` dodaj plik natjmc do folderu.  
  
  Pliki .natjmc to pliki xml z tą składnią:  
  
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
  
 **Atrybuty elementu modułu**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagany. Pełna ścieżka modułu lub modułów. Można użyć symboli wieloznacznych `?` systemu Windows `*` (zero lub jeden znak) i (zero lub więcej znaków). Na przykład:<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> informuje debugera, aby traktować `\3rdParty\UtilLibs` wszystkie moduły na dowolnym dysku jako kod zewnętrzny.|  
|`Company`|Element opcjonalny. Nazwa firmy, która publikuje moduł osadzony w pliku wykonywalnym. Za pomocą tego atrybutu można odróżnić moduły.|  
  
 **Atrybuty elementu pliku**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagany. Pełna ścieżka pliku źródłowego lub plików do traktowania jako kod zewnętrzny. Można używać symboli wieloznacznych `?` systemu Windows i `*` określania ścieżki.|  
  
 **Atrybuty elementu funkcyjnego**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagany. W pełni kwalifikowana nazwa funkcji do traktowania jako kod zewnętrzny.|  
|`Module`|Element opcjonalny. Nazwa lub pełna ścieżka do modułu, który zawiera funkcję. Za pomocą tego atrybutu można odróżnić funkcje o tej samej nazwie.|  
|`ExceptionImplementation`|Po ustawieniu `true`stosu wywołań wyświetla funkcję, która zgłosiła wyjątek, a nie tę funkcję.|  
  
## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a>JavaScript tylko mój kod  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_JS_User_and_non_user_code"></a>Kod użytkownika i osoby niebędące użytkownikiem  
 **Klasyfikacje kodów**  
  
 JavaScript Just My Code kontroluje wyświetlanie stosu krokowego i wywołania, kategoryzując kod w jednej z następujących klasyfikacji:  
  
|||  
|-|-|  
|**MyCode (MyCode)**|Kod użytkownika, którego jesteś właścicielem i który kontrolujesz.|  
|**Kod biblioteki**|Kod niebędący użytkownikiem z bibliotek, których używasz regularnie, a aplikacja polega na poprawne działanie (na przykład WinJS lub jQuery).|  
|**Niepowiązany kod**|Kod niebędący użytkownikiem, który może być uruchomiony w aplikacji, ale nie jest właścicielem, a aplikacja nie polega bezpośrednio na nim, aby działać poprawnie (na przykład sdk reklamowy, który wyświetla reklamy). W projektach ze Sklepu Windows każdy kod, który jest ładowany do aplikacji z identyfikatora URI HTTP lub HTTPS jest również uważany za Niepochlubny Kod.|  
  
 Debuger JavaScript automatycznie klasyfikuje te typy kodu:  
  
- Skrypt, który jest wykonywany przez przekazanie `eval` ciągu do funkcji dostarczonej przez hosta jest klasyfikowany jako **MyCode**.  
  
- Skrypt, który jest wykonywany przez `Function` przekazanie ciągu do konstruktora jest klasyfikowany jako **LibraryCode**.  
  
- Skrypt, który jest zawarty w odwołaniu do struktury, takich jak WinJS lub Azure SDK, jest klasyfikowany jako **LibraryCode**.  
  
- Skrypt wykonywany przez przekazanie ciągu `setTimeout`do `setImmediate`, `setInterval` lub funkcje jest klasyfikowany jako **UnrelatedCode**.  
  
- Określa `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` inny kod użytkownika i nieużywanych dla wszystkich projektów JavaScript programu Visual Studio.  
  
  Domyślne klasyfikacje można zmodyfikować i sklasyfikować określone pliki `mycode.json` i adresy URL, dodawać plik .json o nazwie do folderu głównego projektu.  
  
  Cały inny kod jest klasyfikowany jako **MyCode**.  
  
### <a name="stepping-behavior"></a><a name="BKMK_JS_Stepping_behavior"></a>Zachowanie krokowe  
  
- Jeśli funkcja nie jest użytkownikiem **(MyCode)** kod, **Step Into** (Skrót klawiaturowy: F11) zachowuje się jako **Step Over** (Klawiatura: F10).  
  
- Jeśli krok rozpoczyna się w kodzie niebędącym użytkownikiem **(LibraryCode** lub **UnrelatedCode),** krok po kroku tymczasowo zachowuje się tak, jakby tylko mój kod nie jest włączona. Jak tylko krok wstecz do kodu użytkownika, Tylko mój kod stepping jest ponownie włączone.  
  
- Gdy krok w kodzie użytkownika powoduje pozostawienie bieżącego kontekstu wykonywania (na przykład wykonanie kroku w ostatnim wierszu programu obsługi zdarzeń), debuger zatrzymuje się w następnym wykonywanym wierszu kodu użytkownika. Na przykład jeśli wywołanie zwrotne wykonuje w **kodzie LibraryCode** debuger jest kontynuowany, aż do następnego wiersza kodu użytkownika wykonuje.  
  
- **Step Out** (Keyboard: Shift + F11) zatrzymuje się w następnym wierszu kodu użytkownika. Jeśli nie napotkany kod użytkownika następnie wykonanie jest kontynuowane do momentu zakończenia aplikacji, punkt przerwania zostanie trafiony lub występuje wyjątek.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_JS_Breakpoint_behavior"></a>Zachowanie punktu przerwania  
  
- Punkty przerwania, które zostały ustawione w dowolnym kodzie, będą zawsze trafione niezależnie od klasyfikacji tego kodu  
  
- Jeśli `debugger` słowo kluczowe zostanie napotkane w:  
  
  - **LibraryCode** kod, debuger zawsze przerwy.  

  - **Niepospotrzebalny** kod debuger nie zatrzymuje.  
  
### <a name="exception-behavior"></a><a name="BKMK_JS_Exception_behavior"></a>Zachowanie wyjątku  
 Jeśli wystąpi nieobsługiowany wyjątek w:  
  
- **MyCode** lub **LibraryCode** kod, debuger zawsze przerwy.  
  
- **Niepowiązany** kod Kod i **MyCode** lub **LibraryCode** kod znajduje się na stosie wywołań, debuger przerwy.  
  
  Jeśli wyjątki pierwszej szansy są włączone dla wyjątku w oknie dialogowym Wyjątki, a wyjątek jest zgłaszany w **LibraryCode** lub **Niepospozytowy** kod:  
  
- Jeśli wyjątek jest obsługiwany, debuger nie przerwy.  
  
- Jeśli wyjątek nie jest obsługiwany, debuger przerwy.  
  
### <a name="customize-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a>Dostosowywanie tylko mojego kodu  
 Aby kategoryzować kod użytkownika i osoby niebędącej użytkownikiem dla pojedynczego `mycode.json` projektu programu Visual Studio, dodaj plik .json o nazwie do folderu głównego projektu.  
  
 Klasyfikacje są wykonywane w tej kolejności:  
  
1. Klasyfikacje domyślne  
  
2. Klasyfikacje w `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` pliku  
  
3. Klasyfikacje w `mycode. json` pliku bieżącego projektu.  
  
   Każdy krok klasyfikacji zastępuje poprzednie kroki. Plik .json nie musi wymieniać wszystkich par wartości kluczy, a wartości **MyCode**, **Biblioteki**i **Niepowiązane** mogą być pustymi tablicami.  
  
   Moje pliki Code .json używają tej składni:  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec”,  
        . .  
        "UrlOrFileSpec”  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ]  
}  
  
```  
  
 **Eval, funkcja i ScriptBlock**  
  
 Pary wartości kluczy **Eval**, **Function**i **ScriptBlock** określają sposób klasyfikowania dynamicznie generowanego kodu.  
  
|||  
|-|-|  
|**Eval**|Skrypt, który jest wykonywany przez przekazanie `eval` ciągu do funkcji dostarczonej przez hosta. Domyślnie skrypt Eval jest klasyfikowany jako **MyCode**.|  
|**Funkcja**|Skrypt, który jest wykonywany przez `Function` przekazanie ciągu do konstruktora. Domyślnie skrypt funkcji jest klasyfikowany jako **LibraryCode**.|  
|**Blokada skryptu**|Skrypt, który jest wykonywany przez `setTimeout` `setImmediate`przekazanie `setInterval` ciągu do , lub funkcji. Domyślnie skrypt ScriptBlock jest klasyfikowany jako **UnrelatedCode**.|  
  
 Możesz zmienić wartość na jedno z następujących słów kluczowych:  
  
- `MyCode`klasyfikuje skrypt jako **MyCode**.  
  
- `Library`klasyfikuje skrypt jako **LibraryCode**.  
  
- `Unrelated`klasyfikuje skrypt jako **Niepospokrewniony**.  
  
  **MyCode, biblioteki i niepowiązane**  
  
  Pary wartości **kluczy MyCode**, **Biblioteki**i **Niepowiązane** określają adresy URL lub pliki, które mają zostać uwzględnione w klasyfikacji:  
  
|||  
|-|-|  
|**MyCode (MyCode)**|Tablica adresów URL lub plików, które są klasyfikowane jako **MyCode**.|  
|**Biblioteki**|Tablica adresów URL lub plików, które są klasyfikowane jako **LibraryCode**.|  
|**Niepowiązanych**|Tablica adresów URL lub plików, które są klasyfikowane jako **UnrelatedCode**.|  
  
 Adres URL lub ciąg pliku `*` może zawierać jeden lub więcej znaków, które odpowiadają zero lub więcej znaków. `*`jest odpowiednikiem wyrażenia `.*`regularnego .
