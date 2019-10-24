---
title: Rejestrowanie starszej wersji językowej Językowej2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e1cb2d8193d0ffa6285357634b8bcab549ecbf6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724746"
---
# <a name="registering-a-legacy-language-service"></a>Rejestrowanie starszej wersji usługi językowej
Poniższe sekcje zawierają listę wpisów rejestru dla różnych opcji usługi językowej dostępnych w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Na poniższej liście wpisów rejestru program *vs reg root* jest równy HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X. y*, gdzie *x. y* jest numerem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wersji.

## <a name="registry-entries-for-language-service-options"></a>Wpisy rejestru dotyczące opcji usługi językowej
 Klucz *nazwy języka* Root \Languages\Language\\Services programu *vs reg*może zawierać następujące wartości.

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|(Domyślnie)|REG_SZ|*\<identyfikator GUID >*|Identyfikator GUID usługi językowej.|
|LangResID|REG_DWORD|0x0 — 0xFFFF|Identyfikator zasobu ciągu (ResID) dla zlokalizowanej nazwy tekstu języka.|
|Package|REG_SZ|*\<identyfikator GUID >*|Identyfikator GUID pakietu VSPackage.|
|ShowCompletion|REG_DWORD|0-1|Określa, czy opcje **uzupełniania instrukcji** w oknie dialogowym **Opcje** są włączone.|
|ShowSmartIndent|REG_DWORD|0-1|Określa, czy opcja wyboru **inteligentnego** wcięcia w oknie dialogowym **Opcje** jest włączona.|
|RequestStockColors|REG_DWORD|0-1|Określa, czy kolory niestandardowe lub domyślne są używane do kolorowania słów kluczowych.|
|ShowHotURLs|REG_DWORD|0-1|Określa, czy użytkownik może klikać adresy URL.|
|Domyślne dla nieaktywnych adresów URL|REG_DWORD|0-1|Określa ustawienie początkowe opcji nawigacji po **pojedynczym kliknięciu adresu URL** w oknie dialogowym **Opcje** .|
|DefaultToInsertSpaces|REG_DWORD|0-1|Określa, czy usługa językowa ma opcję "Wstaw spacje" jako domyślną kartę.|
|ShowDropdownBarOption|REG_DWORD|0-1|Włącza lub wyłącza opcję **pasek nawigacyjny** w oknie dialogowym **Opcje** , które pokazuje lub ukrywa **pasek nawigacyjny**.|
|Tylko jedno okno kodu|REG_DWORD|0-1|Włącza lub wyłącza wybór **nowego okna** w menu **okno** dla usługi językowej.|
|EnableAdvancedMembersOption|REG_DWORD|0-1|Włącza lub wyłącza ustawienie okna dialogowego **Opcje** dla opcji **Ukryj zaawansowane elementy członkowskie**.|
|Obsługa CF_HTML|REG_DWORD|0-1|Określa, czy Edytor umożliwia kopiowanie i wklejanie danych HTML.|
|EnableLineNumbersOption|REG_DWORD|0-1|Określa, czy opcje **numerów wierszy** w oknie dialogowym **Opcje** są włączone dla usługi językowej.|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Określa, czy zaawansowane elementy członkowskie, takie jak pola prywatne, są ukryte na listach uzupełniania.|
|ShowBraceCompletion|REG_DWORD|0-1|Określa, czy opcja **uzupełniania nawiasów** w oknie dialogowym **Opcje** jest włączona.|

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

## <a name="registry-entries-for-debugger-languages-options"></a>Wpisy rejestru dotyczące opcji języków debugera
 W programie *vs reg root*\Languages\Language\\Services *nazwa języka \Debugger Languages*\\*GUID*\ Key mogą zawierać następujące wartości.

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|(Domyślnie)|REG_SZ|tekst|Wartość domyślna może służyć do dokumentowania nazwy języka. Nazwa tego klucza jest identyfikatorem GUID ewaluatora wyrażeń, który ma odpowiadający mu wpis w *\<vs reg Root >* \AD7Metrics\Expression ewaluatora.|

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
 Klucze rejestru można dodać w kluczu EditorToolsOptions dla stron właściwości i węzłów właściwości. Te klucze i ich wartości identyfikują strony właściwości w oknie dialogowym **Opcje** (w menu **Narzędzia** ), które są używane do konfigurowania usługi językowej. W poniższym przykładzie *nazwa strony* jest nazwą strony właściwości, a *nazwa węzła* jest nazwą węzła w drzewie okna dialogowego **Opcje** . Wpis strony i wpis węzła muszą być określone osobno.

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|(Domyślnie)|REG_SZ|ResID|Zlokalizowana nazwa wyświetlana tej strony opcji. Nazwa może być tekstem literału lub #`nnn`, gdzie `nnn` jest IDENTYFIKATORem zasobu ciągu w satelickiej bibliotece DLL określonego pakietu VSPackage.|
|Package|REG_SZ|*IDENT*|Identyfikator GUID pakietu VSPackage, który implementuje Tę stronę opcji.|
|Stronic|REG_SZ|*IDENT*|Identyfikator GUID strony właściwości do żądania od pakietu VSPackage przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>. Jeśli ten wpis rejestru nie istnieje, klucz rejestru zawiera opis węzła, a nie strony.|

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

## <a name="registry-entries-for-file-name-extension-options"></a>Wpisy rejestru dotyczące opcji rozszerzenia nazwy pliku
 Wpis dla rozszerzenia pliku powinien zawierać kropkę wiodącą, na przykład ". myext".

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|(Domyślnie)|REG_SZ|*IDENT*|Identyfikator GUID usługi dla domyślnej usługi językowej dla tego typu rozszerzenia nazwy pliku.|

### <a name="example"></a>Przykład

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Wpisy rejestru dla opcji edytora
 Główny klucz \Editors programu *vs reg*może zawierać następujące wartości:

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|(Domyślnie)|REG_SZ|""|Przestrzeń Tutaj możesz umieścić swoją nazwę dokumentacji.|
|DefaultToolboxTab|REG_SZ|""|Nazwa karty przybornika, która ma być domyślna, gdy Edytor jest aktywny.|
|Nazwa|REG_SZ|ResID|Nazwa do wyświetlenia w oknie dialogowym **Otwórz za pomocą** . Nazwa jest IDENTYFIKATORem zasobu ciągu lub nazwą w formacie standardowym.|
|ExcludeDefTextEditor|REG_DWORD|0-1|Używane dla polecenia **Otwórz za pomocą** . Jeśli nie chcesz wyświetlać domyślnego edytora tekstu na liście dostępnych edytorów dla określonego typu pliku, ustaw tę wartość na 1.|
|LinkedEditorGUID|REG_SZ|*\<identyfikator GUID >*|Używane dla każdej usługi językowej, która może otworzyć plik z obsługą strony kodowej. Na przykład po otwarciu pliku txt przy użyciu polecenia **Otwórz za** pomocą opcje są dostępne do użycia w edytorze kodu źródłowego z kodowaniem i bez.<br /><br /> Identyfikator GUID określony w nazwie podklucza jest przeznaczony dla fabryki edytora strony kodowej; połączony identyfikator GUID określony w tym konkretnym wpisie rejestru dotyczy fabryki zwykłych edytorów. Ten wpis polega na tym, że jeśli IDE nie otworzy pliku przy użyciu domyślnego edytora, IDE spróbuje użyć następnego edytora z listy. Ten następny Edytor nie powinien być fabryką edytora strony kodowej, ponieważ ta fabryka edytora jest zasadniczo taka sama jak fabryka edytora, która nie powiodła się.|
|Package|REG_SZ|*\<identyfikator GUID >*|Pakietu VSPackage identyfikator GUID dla ResID nazwy wyświetlanej.|

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

## <a name="registry-entries-for-logical-view-options"></a>Wpisy rejestru dotyczące opcji widoku logicznego
 Interfejs GUI programu *vs reg Root*\\\Editors *Editor >* klucz \LogicalViews może zawierać następujące wartości.

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|(Domyślnie)|REG_SZ||Przestrzeń.|
|*\<identyfikator GUID >*|REG_SZ|""|Klucz do obsługiwanych widoków logicznych. Możesz mieć dowolną tyle rzeczy, ile potrzebujesz. Nazwa wpisu rejestru jest istotna, a nie wartością, która zawsze jest pustym ciągiem.|

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
 Klucz\\\Editors *GUID edytora* *głównego programu vs reg*\Extensions może zawierać następujące wartości. Rozszerzenie nazwy pliku nie zawiera kropki wiodącej.

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|(Domyślnie)|REG_SZ||Przestrzeń.|
|*\<EXT*|REG_DWORD|0 – 0xFFFFFFFF|Względny priorytet rozszerzeń. Jeśli co najmniej dwa języki korzystają z tego samego rozszerzenia, wybierany jest język o wyższym priorytecie.|

 Ponadto domyślny wybór bieżącego użytkownika dla edytora jest przechowywany w HKEY_Current_User\Software\Microsoft\VisualStudio\\*X. Y*\Default editors\\*EXT*. Identyfikator GUID wybranej usługi językowej znajduje się w niestandardowym wpisie. Ma to pierwszeństwo dla bieżącego użytkownika.

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

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Wpisy rejestru dotyczące opcji usługi językowej struktury pakietów zarządzanych
 Następujące wpisy rejestru są specyficzne dla klas usługi języka Managed Package Framework (MPF). Te wpisy rejestru wskazują pomoc techniczną w usłudze językowej dla różnych funkcji IntelliSense i innych zaawansowanych funkcji edycji.

 Te wpisy rejestru są dostępne za pomocą klasy <xref:Microsoft.VisualStudio.Package.LanguagePreferences>.

|Nazwa|Typ|Zakres|Opis|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|Obsługa operacji IntelliSense.|
|MatchBraces|REG_DWORD|0-1|Obsługa pasujących par języków, takich jak nawiasy klamrowe, nawiasy i nawiasy kwadratowe.|
|Sekcji szybkich informacji|REG_DWORD|0-1|Obsługa operacji szybkiej informacji funkcji IntelliSense.|
|ShowMatchingBrace|REG_DWORD|0-1|Obsługa wyświetlania pasującej pary językowej na pasku stanu.|
|MatchBracesAtCaret|REG_DWORD|0-1|Obsługa wyświetlania pasujących par języków, zwykle za pomocą wyróżniania dwóch elementów.|
|MaxErrorMessages|REG_DWORD|0 – n|Maksymalna liczba błędów, które mogą być wyświetlane w oknie **Lista błędów** .|
|CodeSenseDelay|REG_DWORD|0 – n|Liczba milisekund do opóźnienia przed zainicjowaniem analizy w tle dla operacji IntelliSense.|
|EnableAsyncCompletion|REG_DWORD|0-1|Obsługa analizy w tle.|
|EnableCommenting|REG_DWORD|0-1|Obsługa komentowania zaznaczonych bloków tekstu, a także oznacza obsługę usuwania komentarzy do zaznaczonego tekstu.|
|EnableFormatSelection|REG_DWORD|0-1|Obsługa formatowania tekstu, takiego jak automatyczne tworzenie wcięć lub dopasowywanie położenia nawiasów klamrowych.|
|AutoOutlining|REG_DWORD|0-1|Obsługa konspektu (regiony, które mogą być zwinięte).|
|MaxRegions|REG_DWORD|0 – n|Maksymalna liczba ukrytych regionów na plik.|

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

## <a name="see-also"></a>Zobacz także
- [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)