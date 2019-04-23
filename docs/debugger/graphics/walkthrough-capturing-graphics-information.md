---
title: 'Przewodnik: Przechwytywanie informacji graficznych | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd7136367bfb883cfc5d962a1373fec738413fc6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092256"
---
# <a name="walkthrough-capturing-graphics-information"></a>Przewodnik: Przechwytywanie informacji graficznych
W tym instruktażu przedstawiono sposób użycia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagnostyki grafiki, aby ręcznie przechwytywać informacje graficzne z aplikacji Direct3D.

 Ten instruktaż ilustruje następujące zadania:

- Przechwytywanie diagnostyki grafiki do aplikacji

- Przechwytywanie informacji graficznych

## <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych
 Aby korzystać z narzędzi programu Graphics Diagnostics, najpierw musisz przechwytywanie informacji graficznych, która opiera się na. Aby włączyć funkcję przechwytywania, należy użyć **Rozpocznij diagnostykę** polecenie, aby podłączyć Graphics Diagnostics do aplikacji podczas jej uruchamiania.

#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Aby włączyć funkcję przechwytywania informacji graficznych po projekt lub rozwiązanie jest ładowany

1. W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], załaduj plik projektu lub rozwiązania, którą chcesz przechwytywać informacje graficzne z aplikacji.

2. Na pasku narzędzi diagnostyki grafiki, wybierz **Rozpocznij diagnostykę**.

#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Aby włączyć przechwytywanie informacji graficznych bez ładowania projektu lub rozwiązania

1. Na pasku menu wybierz **pliku**, **Otwórz**, **projekt/rozwiązanie**. **Otwórz projekt** pojawi się okno dialogowe.

2. Zamiast pliku projektu lub rozwiązania, należy określić plik wykonywalny aplikacji, który chcesz przechwycić informacje grafiki z, a następnie wybierz **Otwórz**.

3. Na pasku menu wybierz **debugowania**, **grafiki**, **Rozpocznij diagnostykę**.

   Po uruchomieniu aplikacji i jest renderowanie ramki, możesz przechwytywać informacje graficzne.

#### <a name="to-capture-graphics-information"></a>Do przechwytywania informacji graficznych

- Na pasku narzędzi diagnostyki grafiki, wybierz **przechwytywania** przycisku. ![Ikona przycisku przechwytywania grafiki](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")

   —lub—

   Gdy aplikacja w trybie koncentracji uwagi, naciśnij klawisz **klawisza Print Screen**.

  Każdorazowo przechwytywania informacji na temat ramkę, Graphics Diagnostics rejestruje zdarzenia Direct3D i powiązanym stanie i dodaje dane do dziennika grafiki. Nowy dziennik grafiki jest tworzona dla każdej sesji diagnostyki grafiki. Aby uzyskać informacji na temat dzienniki grafiki, zobacz [Przegląd](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu zademonstrowano, jak przechwytywać informacje graficzne ręcznie. Kolejnym krokiem Rozważ użycie tej opcji:

- Dowiedz się, jak analizować przechwycone informacje graficzne przy użyciu narzędzi programu Graphics Diagnostics. Zobacz [Przegląd](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>Zobacz też
- [Przechwytywanie informacji graficznych](capturing-graphics-information.md)