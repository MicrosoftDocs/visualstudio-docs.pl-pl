---
title: Rejestrowanie usługi języka starszego 2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d9d13f301f6c04c0f7b14cc8c685f08b072ef84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705887"
---
# <a name="registering-a-legacy-language-service"></a>Rejestrowanie starszej wersji usługi językowej
W poniższych sekcjach przedstawiono listy wpisów rejestru [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]dla różnych opcji usługi językowej dostępnych w pliku .

 Na poniższej liście wpisów rejestru *katalog główny programu VS Reg* jest równy\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*X.Y*, gdzie *X.Y* jest numerem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wersji.

## <a name="registry-entries-for-language-service-options"></a>Wpisy rejestru dla opcji usługi językowej
 Klucz *języka vs reg root*\\\Languages\Language Services*language name* może zawierać następujące wartości.

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|(Domyślnie)|REG_SZ|*\<>identyfikatorów GUID*|Identyfikator GUID usługi językowej.|
|LangResID ( LangResID )|REG_DWORD|0x0-0xffff|Identyfikator zasobu ciągu (ResID) dla zlokalizowanej nazwy tekstowej języka.|
|Pakiet|REG_SZ|*\<>identyfikatorów GUID*|Identyfikator GUID vspackage.|
|ShowCompletion (ShowCompletion)|REG_DWORD|0-1|Określa, czy opcje **uzupełniania instrukcji** w oknie dialogowym **Opcje** są włączone.|
|Pokaż Wcięcie|REG_DWORD|0-1|Określa, czy opcja **wybierania inteligentnego** wcięcie w oknie dialogowym **Opcje** jest włączona.|
|RequestStockColors (ŻądaniaStockColors)|REG_DWORD|0-1|Określa, czy kolory niestandardowe czy domyślne są używane do kolorowania słów kluczowych.|
|Listy ShowHotURLs|REG_DWORD|0-1|Określa, czy użytkownik może klikać adresy URL.|
|Domyślnie adresy URL niebędące gorącymi adresami URL|REG_DWORD|0-1|Określa ustawienie początkowe opcji **Włącz nawigację z jednym kliknięciem adresu URL** w oknie dialogowym **Opcje.**|
|Obszary DefaultToInsertSpaces|REG_DWORD|0-1|Określa, czy usługa językowa ma "wstaw spacje" jako domyślną opcję karty.|
|ShowDropdownBarOption (PokażdropdownBarOption)|REG_DWORD|0-1|Włącza lub **wyłącza** opcję Pasek nawigacyjny w oknie dialogowym **Opcje,** która pokazuje lub ukrywa **pasek nawigacyjny**.|
|Tylko pojedyncze okno kodu|REG_DWORD|0-1|Włącza lub wyłącza wybór **nowego okna** w menu **Okno** dla usługi językowej.|
|Włącz AdvancedOption członków|REG_DWORD|0-1|Włącza lub wyłącza ustawienie okna dialogowego **Opcje** dla **ukryj członków zaawansowanych**.|
|CF_HTML wsparcia|REG_DWORD|0-1|Określa, czy edytor umożliwia kopiowanie i wklejanie danych HTML.|
|Włącz opcję Włącz liczbę numerów|REG_DWORD|0-1|Określa, czy opcje **numerów wiersza** w oknie dialogowym **Opcje** są włączone dla usługi językowej.|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Określa, czy elementy zaawansowane, takie jak pola prywatne, są ukryte na listach uzupełnień.|
|ShowBraceCompletion (ShowBraceCompletion)|REG_DWORD|0-1|Określa, czy opcja **uzupełnianie nawiasu** klamrowego w oknie dialogowym **Opcje** jest włączona.|

### <a name="example"></a>Przykład

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
        LangResID             = reg_dword:0x00000000
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}
        ShowCompletion        = reg_dword:0x00000001
        ShowSmartIndent       = reg_dword:0x00000001
        ShowDropdownBarOption = reg_dword:0x00000001
```

## <a name="registry-entries-for-debugger-languages-options"></a>Wpisy rejestru dla opcji języków debugera
 Klucz *GUID*\ języka w\\katalogu głównym programu VS Reg \Languages\Language Services*nazwa języka*\Debuger Languages\\*GUID*\ może zawierać następujące wartości.

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|(Domyślnie)|REG_SZ|tekst|Wartość domyślna może służyć do dokumentowania nazwy języka. Nazwa tego klucza jest identyfikatorem GUID oceniającego wyrażenie, * \< *który ma odpowiedni wpis w programie VS Reg Root>\AD7Metrics\Expression Evaluator.|

### <a name="example"></a>Przykład

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        Debugger Languages\
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\
            (Default) = reg_sz:C++
```

## <a name="registry-entries-for-editor-tools-options"></a>Wpisy rejestru dla opcji narzędzi edytora
 Można dodać klucze rejestru w obszarze EditorToolsOptions klucz dla stron właściwości i węzłów właściwości. Te klucze i ich wartości identyfikują strony właściwości w oknie dialogowym **Opcje** (w menu **Narzędzia),** które są używane do konfigurowania usługi językowej. W poniższym *przykładzie nazwa strony* jest nazwą strony właściwości, a *nazwa węzła* jest nazwą węzła w drzewie w oknie dialogowym **Opcje.** Wpis strony i wpis węzła muszą być określone oddzielnie.

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|(Domyślnie)|REG_SZ|Resid|Zlokalizowana nazwa wyświetlana tej strony opcji. Nazwa może być tekst dosłowny lub #`nnn`, gdzie `nnn` jest identyfikator zasobu ciągu w satelicie DLL określonego VSPackage.|
|Pakiet|REG_SZ|*Identyfikator guid*|Identyfikator GUID vspackage, który implementuje tę stronę opcji.|
|Strona|REG_SZ|*Identyfikator guid*|Identyfikator GUID strony właściwości do żądania z VSPackage wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodę. Jeśli ten wpis rejestru nie jest obecny, klucz rejestru opisuje węzeł, a nie stronę.|

### <a name="example"></a>Przykład

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      CSharp\
        EditorToolsOptions\
          Formatting\
            (Default) = reg_sz:#242
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
            General\
              (Default) = reg_sz:#255
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}
            Indentation\
              (Default) = reg_sz:#250
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}
            Newlines\
              (Default) = reg_sz:#253
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}
```

## <a name="registry-entries-for-file-name-extension-options"></a>Wpisy rejestru dla opcji rozszerzenia nazwy pliku
 Wpis rozszerzenia pliku powinien zawierać okres wiodący, na przykład ".myext".

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|(Domyślnie)|REG_SZ|*Identyfikator guid*|Identyfikator GUID usługi dla domyślnej usługi językowej dla tego typu rozszerzenia nazwy pliku.|

### <a name="example"></a>Przykład

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Wpisy rejestru dla opcji edytora
 Klucz *\Editors klucz VS Reg może*zawierać następujące wartości:

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|(Domyślnie)|REG_SZ|""|Nieużywane; możesz umieścić swoje imię i nazwisko tutaj dla dokumentacji.|
|Domyślnatatbox|REG_SZ|""|Nazwa karty przybornika, aby była domyślna, gdy edytor jest aktywny.|
|DisplayName|REG_SZ|Resid|Nazwa do wyświetlenia w oknie dialogowym **Otwieranie za pomocą.** Nazwa jest identyfikatorem zasobu ciągu lub nazwą w formacie standardowym.|
|ExcludeDefTextEditor|REG_DWORD|0-1|Używane dla polecenia menu **Otwórz za pomocą.** Jeśli nie chcesz wystawić domyślnego edytora tekstu na liście dostępnych edytorów dla określonego typu pliku, ustaw tę wartość na 1.|
|PołączonyEditorGUID|REG_SZ|*\<>identyfikatorów GUID*|Używany dla dowolnej usługi językowej, która może otworzyć plik z obsługą strony kodowej. Na przykład po otwarciu pliku txt za pomocą polecenia **Otwórz za** pomocą polecenia Opcje są dostępne dla korzystania z edytora kodu źródłowego z kodowaniem i bez.<br /><br /> Identyfikator GUID określony w nazwie podklucza jest dla fabryki edytora stron kodowych; połączony identyfikator GUID określony w tym konkretnym wpisie rejestru jest przeznaczony dla zwykłej fabryki edytora. Celem tego wpisu jest to, że jeśli IDE nie otwiera pliku przy użyciu edytora domyślnego, IDE spróbuje użyć następnego edytora na liście. Ten następny edytor nie powinien być fabryką edytora stron kodowych, ponieważ ta fabryka edytora jest w zasadzie taka sama jak fabryka edytora, która nie powiodła się.|
|Pakiet|REG_SZ|*\<>identyfikatorów GUID*|Identyfikator GUID vspackage dla identyfikatora rezydowania nazwy wyświetlanej.|

### <a name="example"></a>Przykład

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      (Default)            = reg_sz:Html Editor with Encoding
      DefaultToolboxTab    = reg_sz:HTML
      DisplayName          = reg_sz:#20101
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}
```

## <a name="registry-entries-for-logical-view-options"></a>Wpisy rejestru dla opcji widoku logicznego
 Interfejs *VS Reg Root*GUI\\ *>* \LogicalViews może zawierać następujące wartości.

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|(Domyślnie)|REG_SZ||Nieużywany.|
|*\<>identyfikatorów GUID*|REG_SZ|""|Klucz do obsługiwanych widoków logicznych. Możesz mieć ich tyle, ile potrzebujesz. Nazwa wpisu rejestru jest to, co jest ważne, a nie wartość, która jest zawsze pusty ciąg.|

### <a name="example"></a>Przykład

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      LogicalViews\
       (Default) = reg_sz:
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
```

## <a name="registry-entries-for-editor-extension-options"></a>Wpisy rejestru dla opcji rozszerzenia edytora
 Klucz*GUID*\Extensions programu *VS Reg Root*\Editors\\Editor może zawierać następujące wartości. Rozszerzenie nazwy pliku nie obejmuje okresu wiodącego.

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|(Domyślnie)|REG_SZ||Nieużywany.|
|*\<>wew.*|REG_DWORD|0-0xffffffffff|Względny priorytet rozszerzeń. Jeśli dwa lub więcej języków współużytkuje to samo rozszerzenie, wybierany jest język o wyższym priorytecie.|

 Ponadto domyślny wybór bieżącego użytkownika dla edytora jest przechowywany w\\HKEY_Current_User\Software\Microsoft\VisualStudio*X.Y*\Default Editors\\*ext*. Identyfikator GUID wybranej usługi językowej znajduje się we wpisie Niestandardowy. Ma to pierwszeństwo dla bieżącego użytkownika.

### <a name="example"></a>Przykład

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      Extensions\
       (Default) = reg_sz:
       *         = reg_dword:0x00000018
       html      = reg_dword:0x00000027
       shtm      = reg_dword:0x00000027
       shtml     = reg_dword:0x00000027
```

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Wpisy rejestru dla opcji usługi języka struktury pakietu zarządzanego
 Następujące wpisy rejestru są specyficzne dla klas usługi języka managed package framework (MPF). Te wpisy rejestru wskazują obsługę w usłudze językowej dla różnych funkcji IntelliSense i innych zaawansowanych funkcji edycji.

 Te wpisy rejestru są <xref:Microsoft.VisualStudio.Package.LanguagePreferences> dostępne za pośrednictwem klasy.

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|Nazwa Kodowa|REG_DWORD|0-1|Obsługa operacji IntelliSense.|
|MatchBraces ( MatchBraces )|REG_DWORD|0-1|Obsługa pasujących par języków, takich jak nawiasy klamrowe, nawiasy i nawiasy.|
|Funkcja QuickInfo|REG_DWORD|0-1|Obsługa operacji IntelliSense Quick Info.|
|ShowMatchingBrace (PokażMatchingBrace)|REG_DWORD|0-1|Obsługa wyświetlania pasującej pary języków na pasku stanu.|
|MatchBracesAtCaret ( MatchBracesAtCaret )|REG_DWORD|0-1|Obsługa wyświetlania pasujących par językowych, zazwyczaj poprzez wyróżnianie dwóch elementów.|
|MaxErrorMessages|REG_DWORD|0-n|Maksymalna liczba błędów, które mogą być wyświetlane w oknie **Lista błędów.**|
|Delaj kodowa|REG_DWORD|0-n|Liczba milisekund do opóźnienia przed zainicjowaniem analizy tła dla operacji IntelliSense.|
|EnableAsyncCompletion (Włącz funkcję Nieukończenia)|REG_DWORD|0-1|Obsługa analizowania w tle.|
|Włączkomentowanie|REG_DWORD|0-1|Obsługa komentowania zaznaczonych bloków tekstu, a także oznacza obsługę odkomentowywania zaznaczonego tekstu.|
|Włącz wybór formy|REG_DWORD|0-1|Obsługa formatowania tekstu, takiego jak automatyczne wcięcie lub dostosowywanie położenia nawiasów klamrowych.|
|Automatyczne wykrywanie|REG_DWORD|0-1|Obsługa tworzenia nakreślenia (regiony, które mogą być zwinięte).|
|MaxRegiony|REG_DWORD|0-n|Maksymalna liczba ukrytych regionów na plik.|

```
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      XML\
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}
        MatchBraces           = reg_dword:0x00000001
        QuickInfo             = reg_dword:0x00000001
        ShowMatchingBrace     = reg_dword:0x00000001
        MatchBracesAtCaret    = reg_dword:0x00000000
        MaxErrorMessages      = reg_dword:0x00000064
        CodeSenseDelay        = reg_dword:0x000001f4
        MaxRegions            = reg_dword:0x0000000a
```

## <a name="see-also"></a>Zobacz też
- [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)
