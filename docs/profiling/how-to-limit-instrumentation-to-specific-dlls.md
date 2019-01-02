---
title: 'Instrukcje: Ograniczanie Instrumentacji do określonych bibliotek DLL | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c20dde749f95a24c6d83c7b6693220a5552f89fe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53885171"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Instrukcje: Ograniczanie instrumentacji do określonych bibliotek DLL

Za pomocą metody profilowania instrumentacji, można ograniczyć zbierania danych profilowania do jednego lub więcej bibliotek DLL w aplikacji. Profilowanie jednego lub więcej bibliotek DLL w aplikacji, utwórz sesję wydajności, która zawiera. *dll* pliki jako obiekty docelowe. Można określić bibliotek DLL, które chcesz profilować jako projekty w rozwiązaniu programu Visual Studio lub niezależnie od plików binarnych.

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Ograniczenie Instrumentacji do określonych bibliotek DLL w rozwiązaniu Visual Studio

1. Otwórz rozwiązanie, które zawiera DLL w programie Visual Studio.

2. Na **analizy** menu, wybierz opcję **Uruchom Kreatora wydajności**.

3. Wybierz **Instrumentacji** metody profilowania, a następnie kliknij przycisk **dalej**.

4. Z **które z następujących dostępnych elementów docelowych chcesz profil?**, wybierz nazwę. *Biblioteka DLL* projektu, a następnie kliknij przycisk **dalej**.

5. Kliknij przycisk **Zakończ** aby zakończyć działanie kreatora i wyświetlić nowa sesja wydajności w **Eksplorator wydajności** okna.

6. Kliknij prawym przyciskiem myszy **cele** , a następnie wybierz **Dodaj projekt docelowy**.

7. Z **Dodaj projekt docelowy** listy, wybierz projekt wykonywalny, który chcesz używać do wykonywania pliku DLL.

     Opcjonalna. Możesz dodać wszelkie projekty biblioteki DLL, które mają do profilu.

8. Aby zapobiec zbierania danych dla projektu dodano, kliknij prawym przyciskiem myszy nazwę projektu, a następnie wyczyść **Instrument** pole wyboru.

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Aby określić określonych bibliotek DLL do profilu jako niezależne plików binarnych

1. Otwórz program Visual Studio.

2. Na **analizy** menu, wybierz opcję **Uruchom Kreatora wydajności**.

3. Z **które z następujących dostępnych elementów docelowych chcesz profilu**, wybierz opcję **Profiluj bibliotekę dołączaną dynamicznie (. Biblioteka DLL)** a następnie kliknij przycisk **dalej**.

4. Na drugiej stronie kreatora wykonaj następujące czynności:

    - Wpisz ścieżkę i nazwę. *dll* pliku, który chcesz przeprowadzić profilowanie w **ścieżka biblioteki Dll**. Możesz również kliknąć przycisk wielokropka (...), aby zlokalizować plik w **Biblioteka dołączana dynamicznie do profilowania** okno dialogowe. Należy pamiętać o konieczności podania kopię. *dll* pliku, który będzie uruchamiany przez plik wykonywalny (. *plik exe*) plik, który następnie wybraniu.

    - Wpisz ścieżkę i nazwę pliku wykonywalnego (. *plik exe*) plik, który będzie wykonywać. *dll* w **ścieżka do pliku wykonywalnego**. Możesz również kliknąć przycisk wielokropka (...), aby zlokalizować plik w **pliku wykonywalnego do uruchomienia** okno dialogowe.

    - Opcjonalna. Wpisz wszelkie argumenty wiersza polecenia, które mają być przekazywane do pliku wykonywalnego w **argumenty wiersza polecenia**. Jeśli to konieczne, należy określić katalog roboczy dla aplikacji w **katalog roboczy**.

    - Kliknij przycisk **Dalej**.

5. Wybierz **Instrumentacji** metody profilowania, a następnie kliknij przycisk **dalej**.

6. Kliknij przycisk **Zakończ** aby zakończyć działanie kreatora i wyświetlić nowa sesja wydajności w **Eksplorator wydajności** okna.

7. Opcjonalna. Aby dodać więcej. *dll* plików, kliknij prawym przyciskiem myszy **cele** , a następnie wybierz **Dodaj binarne docelowej**. Wybierz pliki z **Dodaj binarne docelowej** okno dialogowe.

    > [!NOTE]
    > Nie określono pliku wykonywalnego (. *plik exe*) plik, który korzysta z biblioteki dll.

## <a name="see-also"></a>Zobacz także

[Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)  
[Instrukcje: Ograniczenie Instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)