---
title: 'Jak: Ograniczenie oprzyrządowania do określonych bibliotek DLL | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 066262a3fae35e82904b011165813e9dd75d9987
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778820"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Instrukcje: ograniczanie instrumentacji do określonych bibliotek DLL

Za pomocą metody profilowania instrumentacji można ograniczyć zbieranie danych profilowania do co najmniej jednej bibliotek DLL w aplikacji. Aby utworzyć jeden lub więcej bibliotek DLL w aplikacji, należy utworzyć sesję wydajności zawierającą plik . *dll* jako obiekty docelowe. Można określić biblioteki DLL, które mają być profilowane jako projekty w rozwiązaniu programu Visual Studio lub jako niezależne pliki binarne.

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Aby ograniczyć instrumentację do określonych bibliotek DLL w rozwiązaniu programu Visual Studio

1. Otwórz rozwiązanie, które zawiera bibliotekę DLL w programie Visual Studio.

2. W menu **Analiza** wybierz polecenie **Uruchom Kreatora wydajności**.

3. Wybierz **instrumentację** jako metodę profilowania, a następnie kliknij przycisk **Dalej**.

4. Z **którego z poniższych dostępnych celów chcesz profilować?**, wybierz nazwę . projektu *biblioteki dll,* a następnie kliknij przycisk **Dalej**.

5. Kliknij **przycisk Zakończ,** aby zamknąć kreatora i wyświetlić nową sesję wydajności w oknie **Eksploratora wydajności.**

6. Kliknij prawym przyciskiem myszy pozycję **Obiekty docelowe,** a następnie wybierz pozycję **Dodaj projekt docelowy**.

7. Z listy **Dodaj projekt docelowy** wybierz projekt wykonywalny, którego chcesz użyć do wykonania biblioteki DLL.

     Element opcjonalny. Można dodać wszystkie projekty biblioteki DLL, które mają być profilowe.

8. Aby zapobiec zbieraniu danych dla dodanego projektu, kliknij prawym przyciskiem myszy nazwę projektu, a następnie wyczyść pole wyboru **Instrument.**

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Aby określić określone biblioteki DLL do profilu jako niezależne pliki binarne

1. Otwórz program Visual Studio.

2. W menu **Analiza** wybierz polecenie **Uruchom Kreatora wydajności**.

3. Z opcji **Które z poniższych dostępnych obiektów docelowych chcesz utworzyć profil**, wybierz opcję Profil **bibliotekę łączy dynamicznych (. DLL),** a następnie kliknij przycisk **Dalej**.

4. Na drugiej stronie kreatora wykonaj następujące czynności:

    - Wpisz ścieżkę i nazwę pliku pliku . *dll,* który chcesz profilować w **ścieżce Dll**. Można również kliknąć przycisk wielokropka (...) aby zlokalizować plik w **bibliotece łączy dynamicznych do** okna dialogowego profil. Należy pamiętać, że należy określić kopię pliku . *dll,* który zostanie uruchomiony przez plik wykonywalny (.* exe)* wybranego w następnym pliku.

    - Wpisz ścieżkę i nazwę pliku wykonywalnego (.* exe*) plik, który będzie wykonywać . *dll* w **ścieżce wykonywalnej**. Można również kliknąć przycisk wielokropek (...) aby zlokalizować plik w oknie dialogowym **Plik wykonywalny do uruchomienia.**

    - Element opcjonalny. Wpisz wszystkie argumenty wiersza polecenia, które mają zostać przekazano do pliku wykonywalnego w **argumentach wiersza polecenia**. W razie potrzeby określ katalog roboczy aplikacji w **katalogu Roboczym**.

    - Kliknij przycisk **alej**.

5. Wybierz **instrumentację** jako metodę profilowania, a następnie kliknij przycisk **Dalej**.

6. Kliknij **przycisk Zakończ,** aby zamknąć kreatora i wyświetlić nową sesję wydajności w oknie **Eksploratora wydajności.**

7. Element opcjonalny. Aby dodać więcej . *dll,* kliknij prawym przyciskiem myszy pozycję **Cele,** a następnie wybierz polecenie **Dodaj plik binarny docelowy**. Wybierz pliki z okna dialogowego **Dodawanie pliku binarnego docelowego.**

    > [!NOTE]
    > Nie należy określać pliku wykonywalnego (.* exe)* plik, który wykonuje biblioteki DLL.

## <a name="see-also"></a>Zobacz też

[Sterowanie zbieraniem](../profiling/controlling-data-collection.md)
danych[Jak: Ograniczanie oprzyrządowania do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)
