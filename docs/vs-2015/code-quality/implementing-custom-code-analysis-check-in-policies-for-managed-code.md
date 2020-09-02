---
title: Implementowanie niestandardowych zasad ewidencjonowania analizy kodu dla kodu zarządzanego | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1cf759e01e5f152f2220124c90f145bfbbe3c01d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651590"
---
# <a name="implementing-custom-code-analysis-check-in-policies-for-managed-code"></a>Wdrażanie niestandardowych zasad ewidencjonowania analizy kodu dla kodu zarządzanego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zasady ewidencjonowania analizy kodu określają zestaw reguł, które członkowie projektu zespołu muszą uruchomić w kodzie źródłowym, zanim zostaną zaewidencjonowane do kontroli wersji. Firma Microsoft udostępnia zestaw standardowych *zestawów reguł* , które grupują reguły analizy kodu w obszary funkcjonalne. *Niestandardowe zestawy reguł ewidencjonowania* określają zestaw reguł analizy kodu, które są specyficzne dla projektu zespołowego. Zestaw reguł jest przechowywany w pliku. reguł.

 Zasady ewidencjonowania są ustawiane na poziomie projektu zespołowego i określane przez lokalizację pliku. zestawu reguł w drzewie kontroli wersji. Nie ma żadnych ograniczeń dotyczących lokalizacji kontroli wersji zestawu reguł niestandardowych zasad zespołu.

 Analiza kodu jest konfigurowana dla poszczególnych projektów kodu w oknie właściwości dla każdego projektu. Niestandardowy zestaw reguł dla projektu kodu jest określany na podstawie fizycznej lokalizacji pliku. reguł na komputerze lokalnym. Gdy określony jest plik. zestawu reguł, który znajduje się na tym samym dysku co projekt kodu, program Visual Studio używa ścieżki względnej do pliku w konfiguracji projektu.

 Sugerowana metoda tworzenia niestandardowego zestawu reguł projektu zespołowego polega na przechowywaniu pliku zasad ewidencjonowania w specjalnym folderze, który nie jest częścią żadnego projektu kodu. Jeśli plik jest przechowywany w dedykowanym folderze, można zastosować uprawnienia, które ograniczają, kto może edytować plik reguły, i można łatwo przenieść strukturę katalogów, która zawiera projekt do innego katalogu lub komputera.

## <a name="creating-the-team-project-custom-check-in-rule-set"></a>Tworzenie niestandardowego zestawu reguł zaewidencjonowania projektu zespołowego
 Aby utworzyć niestandardowy zestaw reguł dla projektu zespołowego, należy najpierw utworzyć specjalny folder dla reguły zaewidencjonowania dla zestawu zasad w **Eksploator kontroli źródła**. Następnie utworzysz plik zestawu reguł i dodajesz go do kontroli wersji. Na koniec należy określić zestaw reguł jako zasady ewidencjonowania analizy kodu dla projektu zespołowego.

> [!NOTE]
> Aby utworzyć folder w projekcie zespołowym, należy najpierw zmapować główny projekt zespołowy do lokalizacji na komputerze lokalnym. Aby uzyskać więcej informacji, zobacz temat [Tworzenie i współpraca z obszarami roboczymi (stary)](https://msdn.microsoft.com/db4d5692-179a-44fe-ad31-0c1c900c9cb2).

#### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Aby utworzyć folder kontroli wersji dla zestawu reguł zaewidencjonowania

1. W programie [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] rozwiń węzeł projekt zespołowy, a następnie kliknij pozycję **Kontrola źródła**.

2. W okienku **foldery** kliknij prawym przyciskiem myszy projekt zespołowy, a następnie kliknij pozycję **Nowy folder**.

3. W głównym okienku kontroli źródła kliknij prawym przyciskiem myszy pozycję **Nowy folder**, kliknij polecenie **Zmień nazwę**i wpisz nazwę folderu zestawu reguł.

#### <a name="to-create-the-check-in-policy-rule-set"></a>Aby utworzyć zestaw reguł ewidencjonowania

1. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij polecenie **plik**.

2. Na liście **Kategorie** kliknij pozycję **Ogólne**.

3. Na liście **Szablony** kliknij dwukrotnie **zestaw reguł Analiza kodu**.

4. Określ reguły do uwzględnienia w zestawie reguł, a następnie Zapisz plik zestawu reguł w utworzonym folderze zestawu reguł.

     Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych zestawów reguł](../code-quality/creating-custom-code-analysis-rule-sets.md)

#### <a name="to-add-the-rule-set-file-to-version-control"></a>Aby dodać plik zestawu reguł do kontroli wersji

1. W **Eksploator kontroli źródła**kliknij prawym przyciskiem myszy nowy folder, a następnie kliknij polecenie **Dodaj elementy do folderu**.

     Aby uzyskać więcej informacji, zobacz [Korzystanie z kontroli wersji](https://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314).

2. Kliknij utworzony plik zestawu reguł, a następnie kliknij przycisk **Zakończ**.

     Plik zostanie dodany do kontroli źródła i wyewidencjonowany dla Ciebie.

3. W oknie Szczegóły **Eksploator kontroli źródła** kliknij prawym przyciskiem myszy nazwę pliku, a następnie kliknij polecenie **Zaewidencjonuj oczekujące zmiany**.

4. W oknie dialogowym **zaewidencjonowania** możesz dodać komentarz, a następnie kliknąć przycisk **Zaewidencjonuj**.

    > [!NOTE]
    > Jeśli skonfigurowano już zasady zaewidencjonowania analizy kodu dla projektu zespołowego i wybrano opcję **Wymuszaj zaewidencjonowanie tylko do plików, które są częścią bieżącego rozwiązania**, zostanie wyzwolone ostrzeżenie dotyczące błędu zasad. W oknie dialogowym niepowodzenie zasad wybierz opcję **Zastąp błąd zasad i Kontynuuj ewidencjonowanie**. Dodaj wymagany komentarz, a następnie kliknij przycisk **OK**.

#### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Aby określić plik zestawu reguł jako zasady ewidencjonowania

1. W menu **zespół** wskaż polecenie **Ustawienia projektu zespołowego**, a następnie kliknij pozycję **Kontrola źródła**.

2. Kliknij pozycję **zasady ewidencjonowania**, a następnie kliknij przycisk **Dodaj**.

3. Na liście **zasad ewidencjonowania** kliknij dwukrotnie pozycję **Analiza kodu**i upewnij się, że jest zaznaczone pole wyboru **Wymuszaj analizę kodu dla kodu zarządzanego** .

4. Na liście **Uruchom ten zestaw reguł** kliknij pozycję **\<Select Rule Set from Source Control>** .

5. Wpisz ścieżkę pliku zestawu reguł ewidencjonowania w kontroli wersji.

     Ścieżka musi być zgodna z następującą składnią:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > Ścieżkę można skopiować za pomocą jednej z następujących procedur w **Eksploator kontroli źródła**:

    - W okienku **foldery** kliknij folder zawierający plik zestawu reguł. Skopiuj ścieżkę kontroli wersji folderu, który pojawia się w polu **Źródło** , i ręcznie wpisz nazwę pliku zestawu reguł.

    - W oknie Szczegóły kliknij prawym przyciskiem myszy plik zestawu reguł, a następnie kliknij polecenie **Właściwości**. Na karcie **Ogólne** skopiuj wartość w polu **Nazwa serwera**.

## <a name="synchronizing-code-projects-to-the-check-in-policy-rule-set"></a>Synchronizowanie projektów kodu z zestawem reguł zaewidencjonowania
 Zestaw reguł zaewidencjonowania projektu zespołowego jest określany jako zestaw reguł analizy kodu w konfiguracji projektu kodu w oknie dialogowym właściwości projektu kodu. Jeśli zestaw reguł znajduje się na tym samym dysku co projekt kodu, ścieżka względna jest używana do określenia zestawu reguł, gdy ścieżka jest zaznaczona z okna dialogowego plik. Ścieżka względna umożliwia przenośnie ustawień właściwości projektu do innych komputerów, które używają podobnych struktur kontroli wersji lokalnej.

#### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>Aby określić zestaw reguł projektu zespołowego jako zestaw reguł dla projektu kodu

1. W razie potrzeby Pobierz folder i plik zestawu reguł ewidencjonowania z kontroli wersji.

     Ten krok można wykonać w **Eksploator kontroli źródła** , klikając prawym przyciskiem myszy folder zestawu reguł, a następnie klikając polecenie **Pobierz najnowszą wersję**.

2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt kodu, a następnie kliknij polecenie **Właściwości**.

3. **Kliknij pozycję Analiza kodu**.

4. W razie potrzeby kliknij odpowiednie opcje na listach **konfiguracji** i **platformy** .

5. Aby uruchomić analizę kodu przy każdym skompilowaniu projektu kodu przy użyciu określonej konfiguracji, zaznacz pole wyboru **Włącz analizę kodu podczas kompilacji (definiuje stałą CODE_ANALYSIS)** .

6. Aby zignorować kod w składnikach innych firm, zaznacz pole wyboru **Pomiń wyniki z wygenerowanego kodu** .

7. Na liście **Uruchom ten zestaw reguł** kliknij pozycję **\<Browse...>** .

8. Określ lokalną wersję pliku zestawu reguł ewidencjonowania.
