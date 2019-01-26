---
title: Rejestrowanie starszej wersji usługi językowej2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5d65617a354bc5e752d138bc2cf80261ba2736a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955162"
---
# <a name="registering-a-legacy-language-service"></a>Rejestrowanie starszej wersji usługi językowej
Poniższe sekcje zawierają listę wpisów rejestru dla różnych języków opcje usługi dostępne w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Na liście poniżej wpisy rejestru *katalogu głównego rejestru programu VS* jest równa HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, gdzie *X.Y* jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] numer wersji.  
  
## <a name="registry-entries-for-language-service-options"></a>Wpisy rejestru dla opcji usługi w języka  
 *Katalogu głównego rejestru programu VS*usług \Languages\Language\\*Nazwa języka* klucz może zawierać następujących wartości.  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|(Domyślnie)|REG_SZ|*\<GUID>*|Identyfikator GUID usługi języka.|  
|LangResID|REG_DWORD|0x0-0xffff|Ciąg identyfikatora zasobów (ResID) dla nazwy języka zlokalizowanego tekstu.|  
|Package|REG_SZ|*\<GUID>*|Identyfikator GUID pakietu VSPackage.|  
|ShowCompletion|REG_DWORD|0-1|Określa, czy **uzupełniania instrukcji** opcji na liście **opcje** okno dialogowe są włączone.|  
|ShowSmartIndent|REG_DWORD|0-1|Określa, czy możliwość dokonania wyboru **inteligentne** wcięcia w **opcje** okno dialogowe jest włączona.|  
|RequestStockColors|REG_DWORD|0-1|Określa, czy niestandardowe lub domyślne kolory Kolor słów kluczowych.|  
|ShowHotURLs|REG_DWORD|0-1|Określa, czy użytkownik może kliknąć adresów URL.|  
|Domyślnie do adresów URL innych niż gorąca|REG_DWORD|0-1|Określa ustawienia początkowego dla **Włącz nawigację adresów URL jednym kliknięciem** opcji **opcje** okno dialogowe.|  
|DefaultToInsertSpaces|REG_DWORD|0-1|Określa, czy usługa językowa ma "Wstaw miejsca do magazynowania" jako jego opcji karty domyślnej.|  
|ShowDropdownBarOption|REG_DWORD|0-1|Włącza lub wyłącza **pasek nawigacyjny** opcji **opcje** okno dialogowe, które pokazuje lub ukrywa **pasek nawigacyjny**.|  
|Tylko jeden kod okna|REG_DWORD|0-1|Włącza lub wyłącza **nowe okno** choice w **okna** menu dla usługi w języka.|  
|EnableAdvancedMembersOption|REG_DWORD|0-1|Włącza lub wyłącza **opcje** ustawienie okno dialogowe **Ukryj członków zaawansowanych**.|  
|Obsługa CF_HTML|REG_DWORD|0-1|Określa, czy edytor umożliwia kopiowanie i wklejanie danych HTML.|  
|EnableLineNumbersOption|REG_DWORD|0-1|Określa, czy **numery wierszy** opcji na liście **opcje** okno dialogowe jest włączona dla usługi w języka.|  
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Określa, czy członków zaawansowanych, takich jak pola prywatne są ukryte w listach uzupełniania.|  
|ShowBraceCompletion|REG_DWORD|0-1|Określa, czy **uzupełniania nawiasów** opcji **opcje** okno dialogowe jest włączona.|  
  
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
  
## <a name="registry-entries-for-debugger-languages-options"></a>Wpisy rejestru dotyczące języków — opcje debugera  
 *Katalogu głównego rejestru programu VS*usług \Languages\Language\\*Nazwa języka*\Debugger języków\\*GUID*\ klucz może uwzględniać następujące wartości.  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|(Domyślnie)|REG_SZ|tekst|Wartość domyślna może służyć do dokumentowania nazwę języka. Nazwa tego klucza jest identyfikatorem GUID ewaluatora wyrażeń, który ma odpowiadający mu wpis w  *\<VS Reg główny >* \AD7Metrics\Expression ewaluatora.|  
  
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
 Możesz dodać klucze rejestru w kluczu EditorToolsOptions węzłów właściwości i strony właściwości. Te klucze i ich wartości identyfikują strony właściwości w **opcje** okno dialogowe (na **narzędzia** menu), są używane do konfigurowania usługi języka. W poniższym przykładzie *nazwy strony* to nazwa strony właściwości i *nazwa węzła* znajduje się na nazwę węzła w drzewie **opcje** okno dialogowe. Zapis strony i zapis węzła należy określić osobno.  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|(Domyślnie)|REG_SZ|Atrybut resID|Zlokalizowana wyświetlana nazwa ta strona opcji. Nazwa może zawierać tekst dosłowny lub #`nnn`, gdzie `nnn` jest identyfikator zasobu ciągu w towarzyszącej bibliotece DLL z określonego pakietu VSPackage.|  
|Package|REG_SZ|*GUID*|Identyfikator GUID pakietu VSPackage, który implementuje ta strona opcji.|  
|Strona|REG_SZ|*GUID*|Identyfikator GUID strony właściwości, do żądania z pakietu VSPackage, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody. Jeśli tego wpisu rejestru nie jest obecny, klucz rejestru w tym artykule opisano węzła nie strony.|  
  
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
 Wpis dla rozszerzenia pliku powinny zawierać poprzedzone kropką, na przykład ".myext".  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|(Domyślnie)|REG_SZ|*GUID*|Identyfikator GUID usługi Usługa języka domyślnego dla tego typu rozszerzenia nazwy pliku.|  
  
### <a name="example"></a>Przykład  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## <a name="registry-entries-for-editor-options"></a>Wpisy rejestru dla opcji edytora  
 *Katalogu głównego rejestru programu VS*\Editors klucz może zawierać następujących wartości:  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|(Domyślnie)|REG_SZ|""|Nieużywane; Możesz umieścić swoją nazwę, w tym miejscu dla dokumentacji.|  
|DefaultToolboxTab|REG_SZ|""|Nazwa na karcie przybornika, aby ustawić domyślną, gdy edytora jest aktywny.|  
|Nazwa wyświetlana|REG_SZ|Atrybut resID|Nazwa do wyświetlenia w **Otwórz za pomocą** okno dialogowe. Nazwa jest identyfikator ciągu zasobu lub nazwę formatu standardowego.|  
|ExcludeDefTextEditor|REG_DWORD|0-1|Używany do **Otwórz za pomocą** polecenia menu. Jeśli chcesz wyświetlić listę domyślnego edytora tekstu, na liście dostępnych edytorów dla określonego typu pliku, ta wartość 1.|  
|LinkedEditorGUID|REG_SZ|*\<GUID>*|Używane dla dowolnej usługi języka, który można otworzyć pliku z obsługą stronę kodową. Na przykład po otwarciu pliku txt przy użyciu **Otwórz za pomocą** polecenia i opcje są dostarczane do Edytor kodu źródłowego za pomocą oraz bez kodowania.<br /><br /> GUID określony nazwę podklucza który jest stroną kodową fabryki edytora; połączone GUID określony tego wpisu rejestru to fabryki edytora regularne. Celem tego wpisu jest, że jeśli IDE nie można otworzyć pliku przy użyciu domyślnego edytora, IDE podejmie próbę użycia edytora dalej na liście. Ten edytor dalej nie powinien być fabryka edytora strony kodowej, ponieważ tej fabryki edytora jest zasadniczo taki sam jak fabryka edytora, który uległ awarii.|  
|Package|REG_SZ|*\<GUID>*|Identyfikator GUID pakietu VSPackage ResID nazwę wyświetlaną.|  
  
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
  
## <a name="registry-entries-for-logical-view-options"></a>Wpisy rejestru dla opcji Widok logiczny  
 *Katalogu głównego rejestru programu VS*\Editors\\*edytora graficznego interfejsu użytkownika >* \LogicalViews klucz może zawierać następujących wartości.  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|(Domyślnie)|REG_SZ||Nieużywane.|  
|*\<GUID>*|REG_SZ|""|Klucz do logicznych widoków obsługiwane. Może mieć jako wiele z nich, ilu potrzebujesz. Nazwa wpisu rejestru to, co jest ważne, nie wartość, która zawsze jest ciągiem pustym.|  
  
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
  
## <a name="registry-entries-for-editor-extension-options"></a>Wpisy rejestru dla opcji rozszerzenia Edytora  
 *Katalogu głównego rejestru programu VS*\Editors\\*identyfikator GUID edytora*\Extensions klucz może zawierać następujących wartości. Rozszerzenie nazwy pliku nie być poprzedzone kropką.  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|(Domyślnie)|REG_SZ||Nieużywane.|  
|*\<ext >*|REG_DWORD|0 0xffffffff|Względny priorytet rozszerzeń. Jeśli co najmniej dwóch języków udostępniają to samo rozszerzenie, wybranym języku wyższy priorytet.|  
  
 Ponadto, wybór domyślny bieżącego użytkownika dla edytora znajduje się w HKEY_Current_User\Software\Microsoft\VisualStudio\\*X.Y*\Default edytory\\*ext*. Identyfikator GUID usługi wybrany język jest we wpisie niestandardowe. To ma pierwszeństwo przed dla bieżącego użytkownika.  
  
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
  
## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Wpisy rejestru dla opcji usługa języka Framework zarządzanego pakietu  
 Następujące wpisy rejestru są specyficzne dla klas usług językowych framework (MPF) zarządzanego pakietu. Te wpisy rejestru wskazują obsługę w usłudze języka dla różnych funkcji IntelliSense i inne zaawansowane funkcje edycji.  
  
 Te wpisy rejestru są dostępne za pośrednictwem <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy.  
  
|Nazwa|Typ|Zakres|Opis|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0-1|Obsługa operacji IntelliSense.|  
|MatchBraces|REG_DWORD|0-1|Obsługa dopasowane pary języka, takich jak nawiasy klamrowe, nawiasy i nawiasy.|  
|Skrócone informacje|REG_DWORD|0-1|Obsługa operacji szybkie informacje technologii IntelliSense.|  
|ShowMatchingBrace|REG_DWORD|0-1|Obsługa wyświetlania pasującą parę języka na pasku stanu.|  
|MatchBracesAtCaret|REG_DWORD|0-1|Obsługa wyświetlania zgodnych kierunki, zazwyczaj przez wyróżnianie dwóch elementów.|  
|MaxErrorMessages|REG_DWORD|0-n|Maksymalną liczbę błędów, które mogą być wyświetlane w **lista błędów** okna.|  
|CodeSenseDelay|REG_DWORD|0-n|Liczba milisekund, opóźnienie przed rozpoczęciem wszelkich tła analizowanie operacji IntelliSense.|  
|EnableAsyncCompletion|REG_DWORD|0-1|Obsługa analizowanie w tle.|  
|EnableCommenting|REG_DWORD|0-1|Obsługa zakomentowując wybrane bloki tekstu i oznacza również obsługę Trwa usuwanie komentarza do zaznaczonego tekstu.|  
|EnableFormatSelection|REG_DWORD|0-1|Obsługa formatowania tekstu, takie jak automatyczne wcięcie lub dostosowywanie pozycja klamrowych nawiasów.|  
|AutoOutlining|REG_DWORD|0-1|Obsługa konspekt (regiony, które może zostać zwinięty).|  
|MaxRegions|REG_DWORD|0-n|Maksymalna liczba ukrytych regionów na plik.|  
  
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
 [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)