---
title: 'Instrukcje: Tworzenie i edytowanie konfiguracji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5f5d8bb92b80942a95528a0b2e4c7e64bbfafc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668143"
---
# <a name="how-to-create-and-edit-configurations"></a>Porady: tworzenie i edycja konfiguracji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można utworzyć kilka konfiguracji kompilacji dla rozwiązania. Można na przykład skonfigurować kompilację debugowania, która może być używana przez testerów do znajdowania i rozwiązywania problemów, a także skonfigurować różne rodzaje kompilacji, które można dystrybuować do różnych klientów.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="creating-build-configurations"></a>Tworzenie konfiguracji kompilacji
 Za pomocą okna dialogowego **Configuration Manager** można wybrać lub zmodyfikować istniejące konfiguracje kompilacji lub utworzyć nowe.

#### <a name="to-open-the-configuration-manager-dialog-box"></a>Aby otworzyć okno dialogowe Configuration Manager

- W **Eksplorator rozwiązań**Otwórz menu skrótów dla rozwiązania, a następnie wybierz pozycję **Configuration Manager**.

  > [!NOTE]
  > Jeśli polecenie **Configuration Manager** nie pojawia się w menu skrótów, poszukaj w menu **kompilacja** na pasku menu. Jeśli nie pojawia się on na pasku menu, wybierz **Narzędzia**, **Opcje**, a następnie w lewym okienku okna dialogowego **Opcje** , rozwiń węzeł **projekty i rozwiązania**, **Ogólne**i w prawym okienku, zaznacz pole wyboru **Pokaż zaawansowane konfiguracje kompilacji** .

   W oknie dialogowym **Configuration Manager** można użyć listy rozwijanej **aktywna Konfiguracja rozwiązania** , aby wybrać konfigurację kompilacji obejmującą całe rozwiązanie, zmodyfikować istniejącą lub utworzyć nową konfigurację. Możesz użyć listy rozwijanej **Active Solution platform** , aby wybrać platformę, do której należy konfiguracja, zmodyfikować istniejącą lub dodać nową platformę. W okienku **konteksty projektu** wyświetlane są projekty w rozwiązaniu. Dla każdego projektu można wybrać konfigurację i platformę specyficzną dla projektu, zmodyfikować istniejące lub utworzyć nową konfigurację lub dodać nową platformę. Możesz również zaznaczyć pola wyboru wskazujące, czy każdy projekt jest uwzględniany w przypadku używania konfiguracji całego rozwiązania do kompilowania lub wdrażania rozwiązania.

  Po skonfigurowaniu żądanych konfiguracji można ustawić właściwości projektu, które są odpowiednie dla tych konfiguracji.

#### <a name="to-set-properties-based-on-configurations"></a>Aby ustawić właściwości na podstawie konfiguracji

- W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**.

     Zostanie otwarte okno  **strony właściwości** .

     Można ustawić właściwości dla konfiguracji. Na przykład w przypadku konfiguracji wydania można określić, że kod jest zoptymalizowany, gdy rozwiązanie jest skompilowane, a w przypadku konfiguracji debugowania można określić, że `DEBUG` jest włączony symbol kompilacji warunkowej. Aby uzyskać więcej informacji na temat ustawień strony właściwości, zobacz [wprowadzenie do projektanta projektu](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7).

## <a name="creating-and-modifying-project-configurations"></a>Tworzenie i modyfikowanie konfiguracji projektu

#### <a name="to-create-a-project-configuration"></a>Aby utworzyć konfigurację projektu

1. Otwórz okno dialogowe **Configuration Manager** .

2. Wybierz projekt w kolumnie **projekt** .

3. Na liście rozwijanej **Konfiguracja** dla tego projektu wybierz pozycję **Nowy**.

     Zostanie otwarte okno dialogowe **Nowa konfiguracja projektu** .

4. W polu **Nazwa** wprowadź nazwę nowej konfiguracji.

5. Aby użyć ustawień właściwości z istniejącej konfiguracji projektu, na liście rozwijanej **Kopiuj ustawienia z** wybierz konfigurację.

6. Aby utworzyć konfigurację całego rozwiązania w tym samym czasie, zaznacz pole wyboru **Utwórz nową konfigurację rozwiązania** .

#### <a name="to-rename-a-project-configuration"></a>Aby zmienić nazwę konfiguracji projektu

1. Otwórz okno dialogowe **Configuration Manager** .

2. W kolumnie **projekt** wybierz projekt, który ma konfigurację projektu, której nazwę chcesz zmienić.

3. Na liście rozwijanej **Konfiguracja** dla tego projektu wybierz pozycję **Edytuj**.

     **Edytuj konfiguracje projektu** zostanie otwarte okno dialogowe.

4. Wybierz nazwę konfiguracji projektu, którą chcesz zmienić.

5. Wybierz pozycję **Zmień nazwę**, a następnie wprowadź nową nazwę.

## <a name="creating-and-modifying-solution-wide-build-configurations"></a>Tworzenie i modyfikowanie konfiguracji kompilacji obejmujących wiele rozwiązań

#### <a name="to-create-a-solution-wide-build-configuration"></a>Aby utworzyć konfigurację kompilacji obejmującą wiele rozwiązań

1. Otwórz okno dialogowe **Configuration Manager** .

2. Z listy rozwijanej **aktywna Konfiguracja rozwiązania** wybierz pozycję **Nowy**.

     Zostanie otwarte okno dialogowe **Nowa konfiguracja rozwiązania** .

3. W polu tekstowym **Nazwa** wprowadź nazwę nowej konfiguracji.

4. Aby użyć ustawień z istniejącej konfiguracji rozwiązania, na liście rozwijanej **Kopiuj ustawienia z** wybierz konfigurację.

5. Jeśli chcesz utworzyć konfiguracje projektu w tym samym czasie, zaznacz pole wyboru **Utwórz nowe konfiguracje projektu** .

#### <a name="to-rename-a-solution-wide-build-configuration"></a>Aby zmienić nazwę konfiguracji kompilacji dla całego rozwiązania

1. Otwórz okno dialogowe **Configuration Manager** .

2. Z listy rozwijanej **aktywna Konfiguracja rozwiązania** wybierz pozycję **Edytuj**.

     **Edytuj konfiguracje rozwiązania** zostanie otwarte okno dialogowe.

3. Wybierz nazwę konfiguracji rozwiązania, którą chcesz zmienić.

4. Wybierz pozycję **Zmień nazwę**, a następnie wprowadź nową nazwę.

#### <a name="to-modify-a-solution-wide-build-configuration"></a>Aby zmodyfikować konfigurację kompilacji dla całego rozwiązania

1. Otwórz okno dialogowe **Configuration Manager** .

2. Z listy rozwijanej **aktywna Konfiguracja rozwiązania** wybierz żądaną konfigurację.

3. W okienku **konteksty projektu** dla każdego projektu wybierz żądaną **konfigurację** i **platformę** , a następnie wybierz, czy chcesz ją **skompilować** i czy **wdrożyć** .

## <a name="see-also"></a>Zobacz też
 [Informacje o konfiguracjach kompilacji](../ide/understanding-build-configurations.md) [Kompilowanie i czyszczenie projektów oraz rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [NIB How to: modyfikowanie właściwości projektu i ustawień konfiguracji](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
