---
title: 'Instrukcje: Tworzenie i edytowanie konfiguracji'
ms.date: 06/21/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f474adad6d1aaef728c59942fcae17595cd75032
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62824246"
---
# <a name="how-to-create-and-edit-configurations"></a>Instrukcje: Tworzenie i edytowanie konfiguracji

Można utworzyć kilka konfiguracji kompilacji dla rozwiązania. Na przykład można skonfigurować do kompilacji debugowanej, testerom służy do znajdowania i rozwiązywania problemów i można skonfigurować różne rodzaje kompilacji, które mogą być dystrybuowane do różnych klientów.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [tworzenie i edytowanie konfiguracji w programie Visual Studio dla komputerów Mac](/visualstudio/mac/create-and-edit-configurations).

## <a name="create-build-configurations"></a>Utwórz konfiguracje kompilacji

Możesz użyć **programu Configuration Manager** okno dialogowe, wybierz lub zmodyfikowania istniejącej konfiguracji kompilacji lub utworzyć nowe.

Aby otworzyć **programu Configuration Manager** dialogowym **Eksploratora rozwiązań**, otwórz menu skrótów dla rozwiązania, a następnie wybierz **programu Configuration Manager**.

> [!NOTE]
> Jeśli **programu Configuration Manager** polecenie nie pojawi się w menu skrótów, Szukaj w obszarze **kompilacji** menu na pasku menu. Jeśli nie pojawia się ona tam żadnego z nich, na pasku menu wybierz **narzędzia** > **opcje**, a następnie w okienku po lewej stronie **opcje** okna dialogowego rozwiń **Projekty i rozwiązania** > **ogólne**i w okienku po prawej stronie wybierz **Pokaż zaawansowane konfiguracje kompilacji** pole wyboru.

W **programu Configuration Manager** okno dialogowe, można użyć **Konfiguracja rozwiązania aktywnego** listy rozwijanej wybierz konfigurację kompilacji całego rozwiązania, zmodyfikować istniejące lub Utwórz nową Konfiguracja. Możesz użyć **aktywną platformą rozwiązania** listy rozwijanej, aby wybrać platformy, obiekty docelowe konfiguracji, zmodyfikuj istniejącą grupę lub Dodaj nową platformę. **Projektu kontekstów** okienko zawiera listę projektów w rozwiązaniu. Dla każdego projektu można wybrać konfiguracji specyficznych dla projektu i platform, zmodyfikuj istniejące, lub Utwórz nową konfigurację lub Dodaj nową platformę. Możesz również wybrać pola wyboru, które wskazują, czy każdy projekt jest dołączana w przypadku korzystania z konfiguracji całego rozwiązania do kompilacji lub wdrożenia rozwiązania.

 Po skonfigurowaniu konfiguracje, które mają można ustawić właściwości projektu, które są odpowiednie dla tych konfiguracji.

### <a name="set-properties-based-on-configurations"></a>Ustawianie właściwości na podstawie konfiguracji

Aby ustawić właściwości na podstawie konfiguracji, w **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**. Można ustawić właściwości dla Twojej konfiguracji. Na przykład dla konfiguracji wydania, można określić czy kod jest zoptymalizowany, gdy rozwiązanie jest stworzone i dla konfiguracji debugowania, można określić, że `DEBUG` symbol kompilacja warunkowa jest uwzględniany.

Aby uzyskać więcej informacji na temat ustawień strony właściwości, zobacz [Zarządzaj właściwościami projektu i rozwiązania](../ide/managing-project-and-solution-properties.md).

## <a name="create-a-project-configuration"></a>Utwórz konfigurację projektu

1. Otwórz **programu Configuration Manager** okno dialogowe.

2. Wybierz projekt w **projektu** kolumny.

3. W **konfiguracji** listy rozwijanej dla tego projektu, wybierz **New**.

     **Nowa konfiguracja projektu** zostanie otwarte okno dialogowe.

4. W **nazwa** wprowadź nazwę dla nowej konfiguracji.

5. Aby użyć ustawienia właściwości z istniejącej konfiguracji projektu, w **Kopiuj ustawienia** listy rozwijanej wybierz konfigurację.

6. Aby utworzyć konfigurację całego rozwiązania, w tym samym czasie, zaznacz **nowa konfiguracja rozwiązania Utwórz** pole wyboru.

## <a name="rename-a-project-configuration"></a>Zmień nazwę konfiguracji projektu

1. Otwórz **programu Configuration Manager** okno dialogowe.

2. W **projektu** kolumnę, wybierz projekt, który ma konfigurację projektu chcesz zmienić.

3. W **konfiguracji** listy rozwijanej dla tego projektu, wybierz **Edytuj**.

     **Edytuj konfiguracje projektu** zostanie otwarte okno dialogowe.

4. Wybierz nazwę konfiguracji projektu, który chcesz zmienić.

5. Wybierz **Zmień nazwę**, a następnie wprowadź nową nazwę.

## <a name="create-and-modify-solution-wide-build-configurations"></a>Tworzenie i modyfikowanie konfiguracji kompilacji całego rozwiązania

### <a name="to-create-a-solution-wide-build-configuration"></a>Aby utworzyć konfigurację kompilacji całego rozwiązania

1. Otwórz **programu Configuration Manager** okno dialogowe.

2. W **Konfiguracja rozwiązania aktywnego** listy rozwijanej wybierz **New**.

     **Nowa konfiguracja rozwiązania** zostanie otwarte okno dialogowe.

3. W **nazwa** tekstu wprowadź nazwę dla nowej konfiguracji.

4. Aby użyć ustawień z istniejącej konfiguracji rozwiązania, w **Kopiuj ustawienia** listy rozwijanej wybierz konfigurację.

5. Aby utworzyć konfiguracje projektu w tym samym czasie, należy zaznaczyć **Utwórz nowe konfiguracje projektu** pole wyboru.

### <a name="to-rename-a-solution-wide-build-configuration"></a>Aby zmienić konfigurację kompilacji całego rozwiązania

1. Otwórz **programu Configuration Manager** okno dialogowe.

2. W **Konfiguracja rozwiązania aktywnego** listy rozwijanej wybierz **Edytuj**.

     **Edytuj konfiguracje rozwiązania** zostanie otwarte okno dialogowe.

3. Wybierz nazwę konfiguracji rozwiązania, które chcesz zmienić.

4. Wybierz **Zmień nazwę**, a następnie wprowadź nową nazwę.

### <a name="to-modify-a-solution-wide-build-configuration"></a>Aby zmodyfikować konfigurację kompilacji całego rozwiązania

1. Otwórz **programu Configuration Manager** okno dialogowe.

2. W **Konfiguracja rozwiązania aktywnego** listę rozwijaną, wybierz konfigurację ma na liście.

3. W **konteksty projektu** okienko dla każdego projektu, wybierz opcję **konfiguracji** i **platformy** i wybierz opcję **kompilacji**go oraz czy **Wdróż** go.

## <a name="see-also"></a>Zobacz także

- [O konfiguracjach kompilacji](../ide/understanding-build-configurations.md)
- [Kompilowanie i czyszczenie projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Zarządzanie właściwościami projektów i rozwiązań](managing-project-and-solution-properties.md)
- [Tworzenie i edytowanie konfiguracji (Visual Studio dla komputerów Mac)](/visualstudio/mac/create-and-edit-configurations)