---
title: Debuguj kod użytkownika przy użyciu Tylko mój kod | Microsoft Docs
ms.date: 02/13/2019
ms.topic: how-to
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 867477fd3e490f91e81fb91c8be267ede83c8d2c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536568"
---
# <a name="debug-only-user-code-with-just-my-code"></a>Debuguj tylko kod użytkownika z Tylko mój kod

*Tylko mój kod* to funkcja debugowania programu Visual Studio, która automatycznie przechodzi przez wywołania do systemu, platformy i innego kodu niezwiązanego z użytkownikiem. W oknie **stos wywołań** tylko mój kod zwija te wywołania do ramek **[kod zewnętrzny]** .

Tylko mój kod działa inaczej w projektach .NET, C++ i JavaScript.

## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a>Włączać lub wyłączać Tylko mój kod

W przypadku większości języków programowania Tylko mój kod jest domyślnie włączona.

- Aby włączyć lub wyłączyć tylko mój kod w programie Visual Studio, w obszarze **Narzędzia**  >  **Opcje** (lub **Debug**  >  **Opcje**debugowania) > **debugowanie**  >  **Ogólne**, zaznacz lub usuń zaznaczenie opcji **Włącz tylko mój kod**.

![Włącz Tylko mój kod w oknie dialogowym Opcje](../debugger/media/dbg_justmycode_options.png "Włącz Tylko mój kod")

> [!NOTE]
> Wartość **włącz tylko mój kod** to ustawienie globalne, które ma zastosowanie do wszystkich projektów programu Visual Studio we wszystkich językach.

## <a name="just-my-code-debugging"></a>Tylko mój kod, debugowanie

Podczas sesji debugowania w oknie **moduły** są wyświetlane moduły kodu, które debuger jest traktowany jako mój kod (kod użytkownika), wraz ze stanem ładowania symboli. Aby uzyskać więcej informacji, zobacz artykuł [Uzyskaj więcej znajomości, jak debuger dołącza do aplikacji](../debugger/debugger-tips-and-tricks.md#modules_window).

![Kod użytkownika w oknie Moduły](../debugger/media/dbg_justmycode_module.png "Kod użytkownika w oknie Moduły")

W oknie **stos wywołań** lub **zadania** tylko mój kod zwija kod niebędący użytkownikiem do szarej ramki kodu oznaczonej jako adnotacja `[External Code]` .

![Zewnętrzna ramka kodu w oknie stosu wywołań](../debugger/media/dbg_justmycode_externalcode.png "Zewnętrzna ramka kodu")

>[!TIP]
>Aby otworzyć **moduły**, **stos wywołań**, **zadania**lub większość innych okien debugowania, musisz być w sesji debugowania. Podczas debugowania w obszarze **Debug**  >  **okna**debugowania zaznacz okna, które chcesz otworzyć.

<a name="BKMK_Override_call_stack_filtering"></a>Aby wyświetlić kod w ramce zwinięte **[kod zewnętrzny]** , kliknij prawym przyciskiem myszy w oknie **stos wywołań** lub **zadania** i wybierz polecenie **Pokaż kod zewnętrzny** z menu kontekstowego. Rozwinięte zewnętrzne wiersze kodu zastępują ramkę **[kod zewnętrzny**].

![Pokaż kod zewnętrzny w oknie stosu wywołań](../debugger/media/dbg_justmycode_showexternalcode.png "Pokaż kod zewnętrzny")

> [!NOTE]
> **Pokaż kod zewnętrzny** to bieżące ustawienie profilera użytkownika, które ma zastosowanie do wszystkich projektów we wszystkich językach, które są otwierane przez użytkownika.

Dwukrotne kliknięcie rozwiniętego zewnętrznego wiersza kodu w oknie **stosu wywołań** wyróżnia linię kodu wywołującego w kolorze zielonym w kodzie źródłowym. W przypadku bibliotek DLL lub innych modułów, które nie zostały odnalezione lub załadowane, może być otwarta strona nie znaleziono symbolu lub źródła.

## <a name="net-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>Tylko mój kod .NET

W projektach .NET, Tylko mój kod używa plików symboli (*. pdb*) i optymalizacje programu do klasyfikowania kodu użytkownika i niezwiązanego z użytkownikiem. Debuger .NET uwzględnia zoptymalizowane pliki binarne i niezaładowanych plików *. pdb* nie jest kodem użytkownika.

Trzy atrybuty kompilatora wpływają również na to, co jest uznawane za kod użytkownika przez debuger .NET:

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute>informuje debuger, że kod, do którego jest stosowany, nie jest kodem użytkownika.
- <xref:System.Diagnostics.DebuggerHiddenAttribute>ukrywa kod z debugera, nawet jeśli Tylko mój kod jest wyłączone.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute>informuje debuger, aby przeprowadził krok po kodzie, który jest stosowany do, a nie wkroczyć do kodu.

Debuger .NET traktuje wszystkie inne kod jako kod użytkownika.

Podczas debugowania .NET:

- **Debuguj**  >  **Wkrocz do** (lub **F11**) dla kodu niezwiązanego z użytkownikiem w kodzie do następnego wiersza kodu użytkownika.
- **Debuguj**  >  **Wyjdź** (lub **SHIFT** + **F11**) w kodzie nienależącym do użytkownika jest uruchamiany w następnym wierszu kodu użytkownika.

Jeśli nie ma więcej kodu użytkownika, debugowanie będzie kontynuowane do momentu zakończenia, trafień innego punktu przerwania lub zgłasza błąd.

<a name="BKMK_NET_Breakpoint_behavior"></a>Jeśli debuger przerwie się w kodzie nieużywanym przez użytkownika (na przykład w przypadku używania **debugowania**  >  **Break All** i Pause w kodzie innym niż użytkownik) zostanie wyświetlone okno **bez źródła** . Następnie możesz użyć polecenia **Debug**  >  **Step** , aby przejść do następnego wiersza kodu użytkownika.

Jeśli wystąpił nieobsługiwany wyjątek w kodzie innym niż użytkownik, debuger przerwie się w wierszu kodu użytkownika, w którym został wygenerowany wyjątek.

Jeśli wyjątki pierwszej szansy są włączone dla wyjątku, wiersz wywołujący kod użytkownika zostanie wyróżniony kolorem zielonym w kodzie źródłowym. W oknie **stos wywołań** zostanie wyświetlona ramka z adnotacjami z etykietą **[kod zewnętrzny]**.

## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a>Tylko mój kod języka C++

Począwszy od programu Visual Studio 2017 w wersji 15,8, obsługiwane jest również Tylko mój kod do taktowania kodu. Ta funkcja wymaga również użycia przełącznika kompilatora [/JMC (tylko mój kod)](/cpp/build/reference/jmc) . Przełącznik jest domyślnie włączony w projektach C++. W przypadku okna **stosu wywołań** i obsługi stosu wywołań w tylko mój kod przełącznik/JMC nie jest wymagany.

<a name="BKMK_CPP_User_and_non_user_code"></a>Aby można było klasyfikować kod użytkownika, plik PDB dla danych binarnych zawierający kod użytkownika musi zostać załadowany przez debuger (Użyj okna **moduły** , aby to sprawdzić).

W przypadku zachowania stosu wywołań, takiego jak w oknie **stosu wywołań** , tylko mój kod w języku C++ traktuje tylko te funkcje jako kod niebędący *użytkownikiem*:

- Funkcje z usuniętymi informacjami o źródle w ich pliku symboli.
- Funkcja, w której pliki symboli wskazują, że nie ma pliku źródłowego odpowiadającego ramce stosu.
- Funkcje określone w plikach * \* . natjmc* w folderze *%VSInstallDirectory%\Common7\Packages\Debugger\Visualizers* .

W przypadku zachowania przy obchodzeniu kodu Tylko mój kod w języku C++ uwzględnia tylko te funkcje, które *nie są kodem użytkownika*:

- Funkcje, dla których odpowiedni plik PDB nie został załadowany w debugerze.
- Funkcje określone w plikach * \* . natjmc* w folderze *%VSInstallDirectory%\Common7\Packages\Debugger\Visualizers* .

> [!NOTE]
> W przypadku obsługi taktowania kodu w Tylko mój kod kod C++ musi być skompilowany przy użyciu kompilatorów MSVC w programie Visual Studio 15,8 w wersji zapoznawczej 3 lub nowszej, a przełącznik kompilatora/JMC musi być włączony (jest on domyślnie włączony). Aby uzyskać więcej informacji, zobacz [Dostosowywanie stosu wywołań C++ i zachowanie krok po kroku](#BKMK_CPP_Customize_call_stack_behavior)w tym [wpisie w blogu](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/). W przypadku kodu skompilowanego przy użyciu starszego kompilatora pliki *. natstepfilter* są jedynym sposobem dostosowywania kodu, który jest niezależny od tylko mój kod. Zobacz [Dostosowywanie zachowań języka C++](#BKMK_CPP_Customize_stepping_behavior).

<a name="BKMK_CPP_Stepping_behavior"></a>Podczas debugowania języka C++:

- **Debuguj**  >  **Wkrocz do** (lub **F11**) dla kodu niezwiązanego z użytkownikiem w kodzie do następnego wiersza kodu użytkownika.
- **Debuguj**  >  **Wyjdź** (lub **SHIFT** + **F11**) w kodzie nienależącym do użytkownika jest uruchamiany w następnym wierszu kodu użytkownika.

Jeśli nie ma więcej kodu użytkownika, debugowanie będzie kontynuowane do momentu zakończenia, trafień innego punktu przerwania lub zgłasza błąd.

Jeśli debuger przerwie w kodzie nieużywanym przez użytkownika (na przykład w przypadku użycia **debugowania**  >  **Break All** i Pause w kodzie innym niż użytkownik), kontynuacja będzie kontynuowane w kodzie niewykonywanym przez użytkownika.

Jeśli debuger osiągnie wyjątek, zatrzyma się na wyjątku, niezależnie od tego, czy znajduje się on w kodzie użytkownika, czy nie użytkownika. Opcje **nieobsługiwane przez użytkownika** w oknie dialogowym **Ustawienia wyjątku** zostały zignorowane.

### <a name="customize-c-call-stack-and-code-stepping-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a>Dostosowywanie stosu wywołań C++ i zachowań taktowania kodu

W przypadku projektów C++ można określić moduły, pliki źródłowe i funkcje, które okno **stosu wywołań** traktuje się jako kod niebędący użytkownikiem, określając je w plikach * \* . natjmc* . To dostosowanie ma zastosowanie również do taktowania kodu, jeśli używasz najnowszego kompilatora (zobacz [C++ tylko mój kod](#BKMK_CPP_User_and_non_user_code)).

- Aby określić kod niebędący użytkownikiem dla wszystkich użytkowników maszyny programu Visual Studio, Dodaj plik *natjmc* do folderu *%VSInstallDirectory%\Common7\Packages\Debugger\Visualizers* .
- Aby określić kod niebędący użytkownikiem dla pojedynczego użytkownika, Dodaj plik *. natjmc* do folderu *dokumenty%USERPROFILE%\My \\<programie Visual Studio w wersji \> \Visualizers* .

Plik *. natjmc* jest plikiem XML o następującej składni:

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
|`Name`|Wymagany. Pełna ścieżka modułu lub modułów. Możesz użyć symboli wieloznacznych systemu Windows `?` (zero lub jeden znak) i `*` (zero lub więcej znaków). Na przykład<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> nakazuje debugerowi traktowanie wszystkich modułów w *\3rdParty\UtilLibs* na dowolnym dysku jako kod zewnętrzny.|
|`Company`|Opcjonalny. Nazwa firmy, która publikuje moduł osadzony w pliku wykonywalnym. Tego atrybutu można użyć, aby odróżnić moduły.|

 **Atrybuty elementu pliku**

|Atrybut|Opis|
|---------------|-----------------|
|`Name`|Wymagany. Pełna ścieżka pliku źródłowego lub plików, które mają być traktowane jako kod zewnętrzny. Możesz użyć symboli wieloznacznych systemu Windows `?` i `*` podczas określania ścieżki.|

 **Atrybuty elementu funkcji**

|Atrybut|Opis|
|---------------|-----------------|
|`Name`|Wymagany. W pełni kwalifikowana nazwa funkcji, która ma być traktowana jako kod zewnętrzny.|
|`Module`|Opcjonalny. Nazwa lub pełna ścieżka do modułu, który zawiera funkcję. Tego atrybutu można użyć, aby odróżnić funkcje o tej samej nazwie.|
|`ExceptionImplementation`|Po ustawieniu na `true` , stos wywołań wyświetla funkcję, która wywołała wyjątek, a nie tę funkcję.|

### <a name="customize-c-stepping-behavior-independent-of-just-my-code-settings"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a>Dostosuj zachowanie krokowe języka C++ niezależnie od ustawień Tylko mój kod

W projektach C++ można określić funkcje do przekroczenia, wymieniając je jako kod niebędący użytkownikiem w plikach * \* . natstepfilter* . Funkcje wymienione w plikach * \* . natstepfilter* nie są zależne od ustawień tylko mój kod.

- Aby określić kod niebędący użytkownikiem dla wszystkich lokalnych użytkowników programu Visual Studio, Dodaj plik *natstepfilter* do folderu *%VSInstallDirectory%\Common7\Packages\Debugger\Visualizers* .
- Aby określić kod niebędący użytkownikiem dla pojedynczego użytkownika, Dodaj plik *. natstepfilter* do folderu *dokumenty%USERPROFILE%\My \\<programie Visual Studio w wersji \> \Visualizers* .

Plik *. natstepfilter* jest plikiem XML o następującej składni:

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
|`Function`|Wymagany. Określa jedną lub więcej funkcji jako funkcji niebędących użytkownikami.|
|`Name`|Wymagany. Sformatowane wyrażenie regularne ECMA-262 określające pełną nazwę funkcji do dopasowania. Przykład:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> informuje debuger, że wszystkie metody w `MyNS::MyClass` są uznawane za kod niebędący użytkownikiem. W dopasowaniu jest rozróżniana wielkość liter.|
|`Module`|Opcjonalny. Sformatowane wyrażenie regularne ECMA-262 określa pełną ścieżkę do modułu zawierającego funkcję. W dopasowaniu nie jest rozróżniana wielkość liter.|
|`Action`|Wymagany. Jedną z następujących wartości uwzględniających wielkość liter:<br /><br /> `NoStepInto`— informuje debugera, aby przekroczyć funkcję.<br /> `StepInto`— informuje debuger, aby wkraczał do funkcji, zastępując wszystkie inne `NoStepInto` dla dopasowanej funkcji.|

## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a>Tylko mój kod JavaScript

<a name="BKMK_JS_User_and_non_user_code"></a>Język JavaScript Tylko mój kod kontroluje i wywołają Wyświetlanie stosu przez kategoryzację kodu w jednej z tych klasyfikacji:

|Klasyfikacja|Opis|
|-|-|
|**Kod**|Kod użytkownika, który posiadasz i kontrolujesz.|
|**LibraryCode**|Kod niebędący użytkownikiem z bibliotek, które są regularnie używane, a aplikacja polega na poprawnym działaniu (na przykład WinJS lub jQuery).|
|**UnrelatedCode**|Kod niebędący użytkownikiem w aplikacji, który nie jest używany, a aplikacja nie polega na poprawnym działaniu. Na przykład reklamowy zestaw SDK, który wyświetla reklamy, może być UnrelatedCode. W projektach platformy UWP każdy kod, który jest ładowany do aplikacji z identyfikatora URI HTTP lub HTTPS, jest również uznawany za UnrelatedCode.|

Debuger JavaScript klasyfikuje kod jako użytkownika lub niebędący użytkownikiem w następującej kolejności:

1. Domyślne klasyfikacje.
   - Skrypt wykonywany przez przekazanie ciągu do funkcji dostarczonej przez hosta `eval` jest **MyCode**obiektem.
   - Skrypt wykonywany przez przekazanie ciągu do `Function` konstruktora jest **LibraryCode**.
   - Skrypt w dokumentacji platformy, takiej jak WinJS lub zestaw Azure SDK, to **LibraryCode**.
   - Skrypt wykonywany przez przekazanie ciągu do `setTimeout` funkcji, `setImmediate` , lub `setInterval` jest **UnrelatedCode**.

2. Klasyfikacja określona dla wszystkich projektów JavaScript programu Visual Studio w *% VSInstallDirectory% \JavaScript\JustMyCode\mycode.default.wwa.jsw* pliku.

3. Klasyfikacje w *mycode.jsw* pliku bieżącego projektu.

Każdy krok klasyfikacji zastępuje poprzednie kroki.

Wszystkie inne kody są klasyfikowane jako **kod**.

Można modyfikować klasyfikacje domyślne i klasyfikować określone pliki i adresy URL jako kod użytkownika lub niebędący użytkownikami, dodając plik *JSON* o nazwie *mycode.js* do folderu głównego projektu JavaScript. Zobacz [Dostosowywanie języka JavaScript tylko mój kod](#BKMK_JS_Customize_Just_My_Code).

<a name="BKMK_JS_Stepping_behavior"></a>Podczas debugowania JavaScript:

- Jeśli funkcja nie jest kodem użytkownika, krok **debugowania**  >  **do** (lub **F11**) zachowuje się tak samo jak **Debug**  >  **krok** debugowania (lub **F10**).
- Jeśli krok rozpocznie się w kodzie innym niż użytkownik (**LibraryCode** lub **UnrelatedCode**), stopniowy czas działa tak, jakby tylko mój kod nie jest włączona. Gdy powrócisz do kodu użytkownika, Tylko mój kod jest ponownie włączona.
- Gdy krok kodu użytkownika spowoduje opuszczenie bieżącego kontekstu wykonywania, debuger zatrzyma się w następnym wykonanym wierszu kodu użytkownika. Na przykład, jeśli wywołanie zwrotne jest wykonywane w kodzie **LibraryCode** , debuger kontynuuje działanie aż do następnego wiersza kodu użytkownika.
- **Wyjdź** (lub **SHIFT** + **F11**) przestaje w następnym wierszu kodu użytkownika.

Jeśli nie ma więcej kodu użytkownika, debugowanie będzie kontynuowane do momentu zakończenia, trafień innego punktu przerwania lub zgłasza błąd.

Punkty przerwania ustawione w kodzie są zawsze trafień, ale kod jest klasyfikowany.

- Jeśli `debugger` słowo kluczowe występuje w **LibraryCode**, debuger zawsze przerwie.
- Jeśli `debugger` słowo kluczowe występuje w **UnrelatedCode**, debuger nie zatrzyma.

<a name="BKMK_JS_Exception_behavior"></a>Jeśli wystąpił nieobsługiwany wyjątek w kodzie **webcode** lub **LibraryCode** , debuger zawsze przerwie się.

Jeśli wystąpił nieobsługiwany wyjątek w **UnrelatedCode**, a **kod** lub **LibraryCode** znajduje się na stosie wywołań, debuger przerwie.

Jeśli wyjątki pierwszej szansy są włączone dla wyjątku i wystąpi wyjątek w **LibraryCode** lub **UnrelatedCode**:

- Jeśli wyjątek jest obsługiwany, debuger nie przerywa.
- Jeśli wyjątek nie jest obsługiwany, debuger przerwie.

### <a name="customize-javascript-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a>Dostosowywanie Tylko mój kod JavaScript

Aby sklasyfikować kod użytkownika i niebędący użytkownikiem dla jednego projektu JavaScript, można dodać plik *JSON* o nazwie *mycode.js* do folderu głównego projektu.

Specyfikacje w tym pliku przesłaniają klasyfikacje domyślne i *mycode.default.wwa.jsw* pliku. *mycode.jsw* pliku nie musi wyświetlać wszystkich par klucz wartość. Moje **kod**, **biblioteki**i **niepowiązane** wartości mogą być pustymi tablicami.

*Mycode.jsdla* plików użyj następującej składni:

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

**Eval, Function i ScriptBlock**

Pary wartość klucza **eval**, **Function**i **ScriptBlock** określają sposób, w jaki jest klasyfikowany dynamicznie wygenerowany kod:

|Nazwa|Opis|
|-|-|
|**Eval**|Skrypt, który jest wykonywany przez przekazanie ciągu do funkcji dostarczonej przez hosta `eval` . Domyślnie skrypt Eval jest klasyfikowany jako **kod**.|
|**Funkcja**|Skrypt, który jest wykonywany przez przekazanie ciągu do `Function` konstruktora. Domyślnie skrypt funkcji jest klasyfikowany jako **LibraryCode**.|
|**ScriptBlock**|Skrypt, który jest wykonywany przez przekazanie ciągu do `setTimeout` `setImmediate` funkcji,, lub `setInterval` . Domyślnie skrypt ScriptBlock jest klasyfikowany jako **UnrelatedCode**.|

Można zmienić wartość jednego z następujących słów kluczowych:

- `MyCode`klasyfikuje skrypt jako mój **kod**.
- `Library`klasyfikuje skrypt jako **LibraryCode**.
- `Unrelated`klasyfikuje skrypt jako **UnrelatedCode**.

**Moje kod, biblioteki i niepowiązane**

Pary **kod**, **biblioteki**i **niepowiązane** wartości klucza określają adresy URL lub pliki, które mają zostać uwzględnione w klasyfikacji:

|Nazwa|Opis|
|-|-|
|**Kod**|Tablica adresów URL lub plików, które są klasyfikowane jako **kod**.|
|**Biblioteki**|Tablica adresów URL lub plików, które są klasyfikowane jako **LibraryCode**.|
|**Niepowiązanych**|Tablica adresów URL lub plików, które są klasyfikowane jako **UnrelatedCode**.|

Adres URL lub ciąg pliku może mieć co najmniej jeden `*` znak, który pasuje do zera lub więcej znaków. `*`jest taka sama jak wyrażenie regularne `.*` .
