---
title: Implementowanie zasad ewidencjonowania analizy kodu niestandardowego dla zarządzanego kodu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f0b22eabc4df4b6ce7e8596f0c6546cb3a4c61c8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696654"
---
# <a name="implementing-custom-code-analysis-check-in-policies-for-managed-code"></a>Wdrażanie niestandardowych zasad ewidencjonowania analizy kodu dla kodu zarządzanego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analiza kodu, że zasady ewidencjonowania określa zestaw reguł, które członkowie zespołu projektu należy uruchomić na kod źródłowy, przed jego zaewidencjonowaniem do systemu kontroli wersji. Firma Microsoft udostępnia zestaw standardu *zestawów reguł* reguł analizy kodu w tej grupie, do obszarów funkcjonalnych. *Zestawy reguł niestandardowych zasad ewidencjonowania* określić zbiór reguł analizy kodu, które są specyficzne dla projektu zespołowego. Zestaw reguł są przechowywane w plik .ruleset.  
  
 Zasady ewidencjonowania są ustawiane na poziomie projektu zespołu i określone przez lokalizację pliku .ruleset w drzewie kontroli wersji. Nie istnieją żadne ograniczenia dotyczące lokalizacji kontroli wersji team zasad niestandardowego zestawu reguł.  
  
 Analiza kodu jest skonfigurowana dla poszczególnych projektów kodu w oknie dialogowym właściwości dla każdego projektu. Niestandardowy zbiór reguł dla projektu kodu jest określony przez fizyczną lokalizację pliku .ruleset na komputerze lokalnym. Po określeniu plik .ruleset, który znajduje się na tym samym dysku, projekt kodu programu Visual Studio używa ścieżki względnej do pliku w konfiguracji projektu.  
  
 Sugerowane rozwiązanie do tworzenia zespołu projektu niestandardowego zestawu reguł jest przechowywany plik .ruleset zasady ewidencjonowania w folderze specjalnym, który nie jest częścią żadnego projektu kodu. Jeśli plik jest przechowywany w folderze dedykowanej, możesz zastosować uprawnienia, które ograniczają, którzy mogą edytować pliku reguł i można łatwo przenosić struktury katalogów, która zawiera projekt do innego komputera lub katalogu.  
  
## <a name="creating-the-team-project-custom-check-in-rule-set"></a>Tworzenie zestawu niestandardową regułę sprawdzania projektu zespołowego  
 Aby utworzyć niestandardowy zestaw reguł dla projektu zespołowego, należy najpierw utworzyć specjalny folder zestaw reguł zasad ewidencjonowania **Eksploratora kontroli źródła**. Następnie utworzysz pliku zestawu reguł i dodaj go do kontroli wersji. Na koniec należy określić regułę, Ustaw jako zasady analizy kodu ewidencjonowania projektu zespołowego.  
  
> [!NOTE]
> Aby utworzyć folder w projekcie zespołowym, najpierw należy zamapować katalog główny projektu zespołowego do lokalizacji na komputerze lokalnym. Aby uzyskać więcej informacji, zobacz [tworzenie i Praca z obszarami roboczymi (stare)](https://msdn.microsoft.com/db4d5692-179a-44fe-ad31-0c1c900c9cb2).  
  
#### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Aby utworzyć folder kontroli wersji dla zestawu reguł zasad ewidencjonowania  
  
1. W [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], rozwiń węzeł projektu zespołu, a następnie kliknij **kontroli źródła**.  
  
2. W **folderów** okienku kliknij prawym przyciskiem myszy projekt zespołowy, a następnie kliknij przycisk **nowy Folder**.  
  
3. W okienku głównym kontroli źródła, kliknij prawym przyciskiem myszy **nowy Folder**, kliknij przycisk **Zmień nazwę**, a następnie wpisz nazwę dla folderu zestawu reguł.  
  
#### <a name="to-create-the-check-in-policy-rule-set"></a>Aby utworzyć zestaw reguł zasad ewidencjonowania  
  
1. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **pliku**.  
  
2. W **kategorie** kliknij **ogólne**.  
  
3. W **szablony** listy, kliknij dwukrotnie **zestawu reguł analizy kodu**.  
  
4. Określ reguły do uwzględnienia w zestawie reguł, a następnie zapisz plik zestawu reguł do folderu zestawu reguł, który został utworzony.  
  
     Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych zestawów reguł](../code-quality/creating-custom-code-analysis-rule-sets.md)  
  
#### <a name="to-add-the-rule-set-file-to-version-control"></a>Można dodać reguły zestawu plików do kontroli wersji  
  
1. W **Eksploratora kontroli źródła**, kliknij prawym przyciskiem myszy nowy folder, a następnie kliknij przycisk **Dodaj elementy do folderu**.  
  
     Aby uzyskać więcej informacji, zobacz [korzystanie z kontroli wersji](https://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314).  
  
2. Kliknij plik, który został utworzony zestaw reguł, a następnie kliknij **Zakończ**.  
  
     Plik zostanie dodany do kontroli źródła i wyewidencjonowany dla Ciebie.  
  
3. W **Eksploratora kontroli źródła** okno Szczegóły, kliknij prawym przyciskiem myszy nazwę pliku, a następnie kliknij przycisk **Zaewidencjonuj oczekujące zmiany**.  
  
4. W **ewidencjonowania** okno dialogowe, masz opcję, aby dodać komentarz, a następnie kliknij przycisk **Zaewidencjonuj**.  
  
    > [!NOTE]
    > Jeśli zasady analizy kodu ewidencjonowania została już skonfigurowana dla projektu zespołowego i po wybraniu **wymusić zaewidencjonowanie obejmowało tylko pliki, które są częścią bieżącego rozwiązania**, spowoduje wyzwolenie ostrzeżenie o niepowodzeniu zasady. W oknie dialogowym błędu zasad, wybierz **Przesłoń błąd zasad i Kontynuuj ewidencjonowanie**. Dodaj wymagane komentarz, a następnie kliknij przycisk **OK**.  
  
#### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Aby określić regułę Ustaw plik jako zasady ewidencjonowania  
  
1. Na **zespołu** menu wskaż **ustawienia projektu zespołowego**, a następnie kliknij przycisk **kontroli źródła**.  
  
2. Kliknij przycisk **zasad ewidencjonowania**, a następnie kliknij przycisk **Dodaj**.  
  
3. W **zasad ewidencjonowania** listy, kliknij dwukrotnie **analizy kodu**i upewnij się, że **wymusić analizy kodu dla zarządzanego kodu** pole wyboru jest zaznaczone.  
  
4. W **Uruchom ten zestaw reguł** kliknij  **\<z kontroli źródła wybierz zestaw reguł >**.  
  
5. Wpisz ścieżkę pliku zestawu reguł zasad zaewidencjonowania w kontroli wersji.  
  
     Ścieżka musi być zgodna z następującej składni:  
  
     **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    > [!NOTE]
    > Możesz skopiować ścieżkę przy użyciu jednej z poniższych procedur w programie **Eksploratora kontroli źródła**:  
  
    - W **folderów** okienku, kliknij folder zawierający plik zestawu reguł. Kopiuj ścieżkę kontroli wersji, folderu, który pojawia się w **źródła** polu, a następnie wpisz nazwę pliku zestawu reguł ręcznie.  
  
    - W okienku szczegółów kliknij prawym przyciskiem myszy pliku zestawu reguł, a następnie kliknij przycisk **właściwości**. Na **ogólne** kartę, skopiuj wartość w **nazwy serwera**.  
  
## <a name="synchronizing-code-projects-to-the-check-in-policy-rule-set"></a>Synchronizowanie projekty kodu zestawu reguł zasad ewidencjonowania  
 Należy określić regułę zasad ewidencjonowania projektu zespołowego jest ustawiony jako zestaw reguł analizy kodu w konfiguracji projektu kodu w oknie dialogowym właściwości projektu kodu. Jeśli zestaw reguł znajduje się na tym samym dysku, projekt kodu, ścieżka względna jest używana do określania zestawu reguł, gdy ścieżka jest zaznaczona w oknie dialogowym pliku. Ścieżka względna umożliwia ustawienia właściwości projektu, który będzie działał w innych komputerów, które używają podobnych lokalnej wersji kontrolowanie struktury.  
  
#### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>Aby określić regułę projektu zespołowego należy ustawić jako zestaw reguł projektu kodu  
  
1. Jeśli to konieczne, należy pobrać folderu zestawu reguł zasad ewidencjonowania i plików z kontroli wersji.  
  
     Można wykonać tego kroku w **Eksploratora kontroli źródła** przez kliknięcie prawym przyciskiem myszy folder, a następnie klikając polecenie zestawu reguł **Pobierz najnowszą wersję**.  
  
2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt kodu, a następnie kliknij przycisk **właściwości**.  
  
3. **Kliknij przycisk Analiza kodu**.  
  
4. Jeśli to konieczne, kliknij odpowiednie opcje w **konfiguracji** i **platformy** listy.  
  
5. Aby uruchomić analizę kodu, ilekroć dany projekt kodu został skompilowany przy użyciu określonej konfiguracji, zaznacz **Włącz analizę kodu podczas kompilacji (definiuje stałą CODE_ANALYSIS)** pole wyboru.  
  
6. Ignorowanie kodu w składników innych firm, wybierz **Pomijaj wyniki z wygenerowanego kodu** pole wyboru.  
  
7. W **Uruchom ten zestaw reguł** kliknij  **\<Przeglądaj … >**.  
  
8. Określ lokalną wersję pliku zestawu reguł zasad ewidencjonowania.
