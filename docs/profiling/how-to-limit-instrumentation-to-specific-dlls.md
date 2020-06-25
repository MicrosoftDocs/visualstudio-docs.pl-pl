---
title: Jak ograniczyć instrumentację do określonych bibliotek DLL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 391aeb0b1686d58116d6aaa52ad0a3defe15fb00
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85327799"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Instrukcje: ograniczanie instrumentacji do określonych bibliotek DLL

Korzystając z metody profilowania instrumentacji, można ograniczyć zbieranie danych profilowania do co najmniej jednej biblioteki DLL w aplikacji. Aby profilować co najmniej jedną bibliotekę DLL w aplikacji, należy utworzyć sesję wydajności obejmującą. pliki *dll* jako elementy docelowe. Możesz określić biblioteki DLL, które chcesz profilować jako projekty w rozwiązaniu programu Visual Studio lub jako niezależne pliki binarne.

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Aby ograniczyć instrumentację do określonych bibliotek DLL w rozwiązaniu programu Visual Studio

1. Otwórz rozwiązanie, które zawiera plik DLL w programie Visual Studio.

2. W menu **Analizuj** wybierz pozycję **Uruchom Kreatora wydajności**.

3. Wybierz **instrumentację** jako metodę profilowania, a następnie kliknij przycisk **dalej**.

4. Z **następujących dostępnych elementów docelowych chcesz profilować?** wybierz nazwę. *dll* , a następnie kliknij przycisk **dalej**.

5. Kliknij przycisk **Zakończ** , aby zamknąć kreatora i wyświetlić nową sesję wydajności w oknie **Eksplorator wydajności** .

6. Kliknij prawym przyciskiem myszy element **docelowy** , a następnie wybierz polecenie **Dodaj projekt docelowy**.

7. Z listy **Dodaj projekt docelowy** wybierz projekt wykonywalny, który ma być używany do korzystania z biblioteki DLL.

     Opcjonalny. Możesz dodać wszystkie projekty DLL, które chcesz profilować.

8. Aby uniemożliwić zbieranie danych dla dodanego projektu, kliknij prawym przyciskiem myszy nazwę projektu, a następnie wyczyść pole wyboru **instrument** .

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Aby określić określone biblioteki DLL do profilowania jako niezależne pliki binarne

1. Otwórz program Visual Studio.

2. W menu **Analizuj** wybierz pozycję **Uruchom Kreatora wydajności**.

3. Z **następujących dostępnych elementów docelowych chcesz profilować**, wybierz **profil biblioteka dołączana dynamicznie (. DLL)** , a następnie kliknij przycisk **dalej**.

4. Na drugiej stronie kreatora wykonaj następujące czynności:

    - Wpisz ścieżkę i nazwę pliku. plik *dll* , który ma być profilem w **ścieżce dll**. Możesz również kliknąć przycisk wielokropka (...), aby zlokalizować plik w oknie dialogowym **biblioteka dołączana dynamicznie do profilowania** . Należy pamiętać, że należy określić kopię. plik *dll* , który będzie uruchamiany przez plik wykonywalny (.* exe*), który wybierzesz dalej.

    - Wpisz ścieżkę i nazwę pliku wykonywalnego (.* exe*), który będzie wykonywał. *Biblioteka DLL* w **ścieżce pliku wykonywalnego**. Możesz również kliknąć przycisk wielokropka (...), aby zlokalizować plik w oknie dialogowym **plik wykonywalny do uruchomienia** .

    - Opcjonalny. Wpisz wszystkie argumenty wiersza polecenia, które chcesz przekazać do pliku wykonywalnego w **argumentach wiersza polecenia**. W razie potrzeby określ katalog roboczy aplikacji w **katalogu roboczym**.

    - Kliknij przycisk **Dalej**.

5. Wybierz **instrumentację** jako metodę profilowania, a następnie kliknij przycisk **dalej**.

6. Kliknij przycisk **Zakończ** , aby zamknąć kreatora i wyświetlić nową sesję wydajności w oknie **Eksplorator wydajności** .

7. Opcjonalny. , Aby dodać więcej. pliki *dll* , kliknij prawym przyciskiem myszy **obiekt docelowy** , a następnie wybierz polecenie **Dodaj docelowy plik binarny**. Wybierz pliki z okna dialogowego **Dodaj docelowy plik binarny** .

    > [!NOTE]
    > Nie określaj pliku wykonywalnego (.* exe*), który wykonuje pliki dll.

## <a name="see-also"></a>Zobacz też

Zbieranie danych sterujących [Control data collection](../profiling/controlling-data-collection.md) 
 [Instrukcje: ograniczanie instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)
