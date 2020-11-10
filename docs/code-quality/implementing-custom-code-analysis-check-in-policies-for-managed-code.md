---
title: Niestandardowe zasady ewidencjonowania analizy kodu dla kodu zarządzanego
ms.date: 11/04/2016
description: Dowiedz się, jak utworzyć niestandardowe zasady ewidencjonowania analizy kodu. Zobacz, jak upewnić się, że kod zarządzany przez program Visual Studio jest zgodny z zasadami projektu usługi Azure DevOps.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 567b6d2fe8906fd1a7a07ab73835439f8a9a9955
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435427"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementowanie niestandardowych zasad zaewidencjonowania analizy kodu dla kodu zarządzanego

Zasady ewidencjonowania analizy kodu określają zestaw reguł, które członkowie projektu usługi Azure DevOps muszą uruchomić w kodzie źródłowym, zanim zostaną zaewidencjonowane do kontroli wersji. Firma Microsoft udostępnia zestaw standardowych *zestawów reguł* , które grupują reguły analizy kodu w obszary funkcjonalne. *Niestandardowe zestawy reguł ewidencjonowania* określają zestaw reguł analizy kodu, które są specyficzne dla projektu. Zestaw reguł jest przechowywany w pliku. reguł.

Zasady ewidencjonowania są ustawiane na poziomie projektu usługi Azure DevOps i określane przez lokalizację pliku. zestawu reguł w drzewie kontroli wersji. Nie ma żadnych ograniczeń dotyczących lokalizacji kontroli wersji zestawu reguł niestandardowych zasad zespołu.

Analiza kodu jest konfigurowana dla poszczególnych projektów kodu w oknie właściwości dla każdego projektu. Niestandardowy zestaw reguł dla projektu kodu jest określany na podstawie fizycznej lokalizacji pliku. reguł na komputerze lokalnym. Gdy określony jest plik. zestawu reguł, który znajduje się na tym samym dysku co projekt kodu, program Visual Studio używa ścieżki względnej do pliku w konfiguracji projektu.

Sugerowana metoda tworzenia zestawu reguł niestandardowych projektu usługi Azure DevOps polega na przechowywaniu pliku zasad ewidencjonowania w specjalnym folderze, który nie jest częścią żadnego projektu kodu. Jeśli plik jest przechowywany w dedykowanym folderze, można zastosować uprawnienia, które ograniczają, kto może edytować plik reguły, i można łatwo przenieść strukturę katalogów, która zawiera projekt do innego katalogu lub komputera.

## <a name="create-the-project-custom-check-in-rule-set"></a>Tworzenie niestandardowego zestawu reguł ewidencjonowania projektu

Aby utworzyć niestandardowy zestaw reguł dla projektu usługi Azure DevOps, należy najpierw utworzyć specjalny folder dla reguły zasad ewidencjonowania w **Eksploator kontroli źródła**. Następnie utworzysz plik zestawu reguł i dodajesz go do kontroli wersji. Na koniec należy określić regułę ustawioną jako zasady ewidencjonowania analizy kodu dla projektu.

> [!NOTE]
> Aby utworzyć folder w projekcie usługi Azure DevOps, należy najpierw zmapować katalog główny projektu do lokalizacji na komputerze lokalnym.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Aby utworzyć folder kontroli wersji dla zestawu reguł zaewidencjonowania

1. W Team Explorer rozwiń węzeł projektu, a następnie kliknij pozycję **Kontrola źródła**.

2. W okienku **foldery** kliknij prawym przyciskiem myszy projekt, a następnie kliknij pozycję **Nowy folder**.

3. W głównym okienku kontroli źródła kliknij prawym przyciskiem myszy pozycję **Nowy folder** , kliknij polecenie **Zmień nazwę** i wpisz nazwę folderu zestawu reguł.

### <a name="to-create-the-check-in-policy-rule-set"></a>Aby utworzyć zestaw reguł ewidencjonowania

1. W menu **plik** wskaż polecenie **Nowy** , a następnie kliknij polecenie **plik**.

2. Na liście **Kategorie** kliknij pozycję **Ogólne**.

3. Na liście **Szablony** kliknij dwukrotnie **zestaw reguł Analiza kodu**.

4. [Określ reguły](../code-quality/how-to-create-a-custom-rule-set.md) do uwzględnienia w zestawie reguł, a następnie Zapisz plik zestawu reguł w utworzonym folderze zestawu reguł.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Aby dodać plik zestawu reguł do kontroli wersji

1. W **Eksploator kontroli źródła** kliknij prawym przyciskiem myszy nowy folder, a następnie kliknij polecenie **Dodaj elementy do folderu**.

     Aby uzyskać więcej informacji, zobacz [git i Azure Repos](/azure/devops/repos/git/overview?view=vsts&preserve-view=true).

2. Kliknij utworzony plik zestawu reguł, a następnie kliknij przycisk **Zakończ**.

     Plik zostanie dodany do kontroli źródła i wyewidencjonowany dla Ciebie.

3. W oknie Szczegóły **Eksploator kontroli źródła** kliknij prawym przyciskiem myszy nazwę pliku, a następnie kliknij polecenie **Zaewidencjonuj oczekujące zmiany**.

4. W oknie dialogowym **zaewidencjonowania** możesz dodać komentarz, a następnie kliknąć przycisk **Zaewidencjonuj**.

    > [!NOTE]
    > Jeśli skonfigurowano już zasady ewidencjonowania analizy kodu dla projektu usługi Azure DevOps, a zaznaczono opcję **Wymuszaj tylko pliki będące częścią bieżącego rozwiązania** , zostanie wyzwolone ostrzeżenie dotyczące błędu zasad. W oknie dialogowym niepowodzenie zasad wybierz opcję **Zastąp błąd zasad i Kontynuuj ewidencjonowanie**. Dodaj wymagany komentarz, a następnie kliknij przycisk **OK**.

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Aby określić plik zestawu reguł jako zasady ewidencjonowania

1. W menu **zespół** wskaż pozycję **Ustawienia projektu** , a następnie kliknij pozycję **Kontrola źródła**.

2. Kliknij pozycję **zasady ewidencjonowania** , a następnie kliknij przycisk **Dodaj**.

3. Na liście **zasad ewidencjonowania** kliknij dwukrotnie pozycję **Analiza kodu** i upewnij się, że jest zaznaczone pole wyboru **Wymuszaj analizę kodu dla kodu zarządzanego** .

4. Na liście **Uruchom ten zestaw reguł** kliknij pozycję **\<Select Rule Set from Source Control>** .

5. Wpisz ścieżkę pliku zestawu reguł ewidencjonowania w kontroli wersji.

     Ścieżka musi być zgodna z następującą składnią:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > Ścieżkę można skopiować za pomocą jednej z następujących procedur w **Eksploator kontroli źródła** :

    - W okienku **foldery** kliknij folder zawierający plik zestawu reguł. Skopiuj ścieżkę kontroli wersji folderu, który pojawia się w polu **Źródło** , i ręcznie wpisz nazwę pliku zestawu reguł.

    - W oknie Szczegóły kliknij prawym przyciskiem myszy plik zestawu reguł, a następnie kliknij polecenie **Właściwości**. Na karcie **Ogólne** skopiuj wartość w polu **Nazwa serwera**.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Synchronizuj projekty kodu z zestawem reguł zaewidencjonowania

Należy określić regułę zasad ewidencjonowania projektu jako zestaw reguł analizy kodu w konfiguracji projektu kodu w oknie dialogowym właściwości projektu kodu. Jeśli zestaw reguł znajduje się na tym samym dysku co projekt kodu, ścieżka względna jest używana do określenia zestawu reguł, gdy ścieżka jest zaznaczona z okna dialogowego plik. Ścieżka względna umożliwia przenośnie ustawień właściwości projektu do innych komputerów, które używają podobnych struktur kontroli wersji lokalnej.

### <a name="to-specify-a-project-rule-set-as-the-rule-set-of-a-code-project"></a>Aby określić zestaw reguł projektu jako zestaw reguł projektu kodu

1. W razie potrzeby Pobierz folder i plik zestawu reguł ewidencjonowania z kontroli wersji.

   Ten krok można wykonać w **Eksploator kontroli źródła** , klikając prawym przyciskiem myszy folder zestawu reguł, a następnie klikając polecenie **Pobierz najnowszą wersję**.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt kodu, a następnie kliknij polecenie **Właściwości**.

3. **Kliknij pozycję Analiza kodu**.

4. W razie potrzeby kliknij odpowiednie opcje na listach **konfiguracji** i **platformy** .

::: moniker range="vs-2017"

5. Aby uruchomić analizę kodu przy każdym skompilowaniu projektu kodu przy użyciu określonej konfiguracji, wybierz opcję **Włącz analizę kodu podczas kompilacji**.

::: moniker-end

::: moniker range=">=vs-2019"

5. Aby uruchomić analizę kodu przy każdym skompilowaniu projektu kodu przy użyciu określonej konfiguracji, wybierz pozycję **Uruchom przy kompilacji** w sekcji **analizatory binarne** .

::: moniker-end

6. Na liście **Uruchom ten zestaw reguł** kliknij pozycję **\<Browse>** .

8. Wybierz lokalną wersję pliku zestawu reguł ewidencjonowania.
