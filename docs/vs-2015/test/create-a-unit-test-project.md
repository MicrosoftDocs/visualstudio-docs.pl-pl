---
title: Tworzenie projektu testu jednostkowego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: a608bfba-1a43-4a60-b73a-1fe53ef58098
caps.latest.revision: 10
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bfc85b0616fdf8f30732f2409a1a15040967dbb3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660650"
---
# <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Testy jednostkowe często duplikują strukturę testowanego kodu. Na przykład projekt testu jednostkowego zostanie utworzony dla każdego projektu kodu w produkcie. Projekt testowy może być w tym samym rozwiązaniu co kod produkcyjny lub może znajdować się w osobnym rozwiązaniu. W rozwiązaniu można mieć wiele projektów testów jednostkowych.

> [!NOTE]
> Lokalizacja testów jednostkowych dla kodu natywnego i struktury projektu testowego może różnić się od struktury opisanej w tym temacie. Aby uzyskać więcej informacji, zobacz [Dodawanie testów jednostkowych do istniejących aplikacji C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md).

## <a name="to-create-a-unit-test-project"></a>Aby utworzyć projekt testu jednostkowego:

1. W menu **plik** wybierz polecenie **Nowy** , a następnie wybierz **projekt** (klawiatura Ctrl + Shift + N).

2. W oknie dialogowym Nowy projekt rozwiń węzeł **zainstalowany** , wybierz język, który ma być używany dla projektu testowego, a następnie wybierz polecenie **Testuj**.

3. Aby użyć jednej z platform testów jednostkowych firmy Microsoft, wybierz opcję **projekt testu jednostkowego** z listy szablonów projektu. W przeciwnym razie wybierz szablon projektu dla struktury testów jednostkowych, który ma być używany. Aby przetestować projekt kont w naszym przykładzie, należy nazwać projekt AccountsTests.

4. W projekcie testów jednostkowych Dodaj odwołanie do testowanego kodu.  Poniżej przedstawiono sposób tworzenia odwołania do projektu kodu w tym samym rozwiązaniu:

    1. Wybierz projekt w Eksplorator rozwiązań.

    2. W menu **projekt** wybierz polecenie **Dodaj odwołanie..**..

    3. W oknie dialogowym Menedżer odwołań Otwórz węzeł **rozwiązania** i wybierz pozycję **projekty**. Sprawdź nazwę projektu kodu i Zamknij okno dialogowe.

5. Jeśli kod, który ma zostać przetestowany, znajduje się w innej lokalizacji, zobacz [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md) , aby uzyskać informacje na temat dodawania odwołań.

## <a name="next-steps"></a>Następne kroki
 **Pisanie testów jednostkowych**

 Zobacz jedną z następujących sekcji:

- [Pisanie testów jednostkowych dla .NET Framework za pomocą struktury testów jednostkowych Microsoft dla kodu zarządzanego](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)

- [Pisanie testów jednostkowych dla języka C/C++ za pomocą platformy testów jednostkowych firmy Microsoft dla języka C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)

  **Uruchamianie testów jednostkowych**

  [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)
