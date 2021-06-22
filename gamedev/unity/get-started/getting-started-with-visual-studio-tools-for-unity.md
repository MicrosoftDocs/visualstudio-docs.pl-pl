---
title: Wprowadzenie z Visual Studio Tools for Unity | Microsoft Docs
description: Dowiedz się, jak instalować i instalować Visual Studio do budowania aplikacji unity.
ms.date: 01/27/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
zone_pivot_groups: platform
ms.openlocfilehash: 706700c8343d934f7a9a5ce32f98bf96e67d4259
ms.sourcegitcommit: 07e6db4bf2966863093e3974c60c3b46e6953416
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2021
ms.locfileid: "112488848"
---
# <a name="get-started-with-visual-studio-and-unity"></a>Wprowadzenie do Visual Studio i aparatu Unity

> [!NOTE]
> W tym przewodniku przyjęto założenie, że zainstalowano już unity przy użyciu programu Unity Hub. Jeśli jesteś nowym użytkownikom aparatu Unity, zalecamy odwiedzenie strony Unity Learn i ukończenie ścieżki szkoleniowej [Unity Essentials.](https://learn.unity.com/pathway/unity-essentials)

## <a name="install-unity-support-for-visual-studio"></a>Instalowanie obsługi aparatu Unity dla Visual Studio

Visual Studio Tools for Unity to bezpłatne rozszerzenie, które zapewnia obsługę pisania i debugowania języka C# i nie tylko. Odwiedź stronę [Przeglądu narzędzi dla aparatu Unity,](./visual-studio-tools-for-unity.md) aby uzyskać pełną listę informacji o rozszerzeniach.

:::zone pivot="windows"

> [!NOTE]
> Ten przewodnik instalacji jest dla Visual Studio. Jeśli używasz aplikacji, Visual Studio Code unity development with VS Code documentation (Tworzenie aplikacji na platformie [Unity przy użyciu VS Code dokumentacji).](https://code.visualstudio.com/docs/other/unity)

1. [Pobierz instalatora Visual Studio lub](/visualstudio/install/install-visual-studio.md)uruchom go, jeśli został już zainstalowany.
2. Kliknij **pozycję Modyfikuj** (jeśli jest już zainstalowana) lub **Zainstaluj** (w przypadku nowych instalacji) dla żądanej wersji Visual Studio.
3. Na karcie **Workloads (Obciążenia)** przewiń do sekcji **Gaming (Gry)** i wybierz obciążenie **Game development with Unity (Opracowywanie gier za pomocą aparatu Unity).**

    ![Okno obciążenia tworzenia gier za pomocą aparatu Unity w instalatorze](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> Ten przewodnik instalacji jest dla Visual Studio dla komputerów Mac. Jeśli używasz aplikacji, Visual Studio Code unity development with VS Code documentation (Tworzenie aplikacji na platformie [Unity przy użyciu VS Code dokumentacji).](https://code.visualstudio.com/docs/other/unity)

Narzędzia dla aparatu Unity są dołączone do instalacji Visual Studio dla komputerów Mac i nie są wymagane żadne oddzielne kroki instalacji. Możesz to sprawdzić w **Visual Studio dla komputerów Mac > Extensions > Game Development.** **Visual Studio dla komputerów Mac tools for Unity** powinny być włączone.

![Widok Menedżera rozszerzeń z włączonymi Visual Studio dla komputerów Mac Tools for Unity](../media/vsm/unity-workload.png)

:::zone-end

## <a name="check-for-updates"></a>Sprawdź aktualizacje

Zaleca się, aby aktualizacje Visual Studio i Visual Studio dla komputerów Mac były aktualizowane, aby mieć najnowsze poprawki usterek, funkcje i obsługę aparatu Unity. Nie wymaga to aktualizacji wersji aparatu Unity.

:::zone pivot="windows"

1. Kliknij menu **Pomoc > Sprawdź aktualizacje.**

    ![Menu Sprawdzanie aktualizacji w programie Visual Studio 2019](../media/vs/check-for-updates.png)

2. Jeśli jest dostępna aktualizacja, Instalator programu Visual Studio zostanie pokazana nowa wersja. Kliknij przycisk **Aktualizuj.**

:::zone-end
:::zone pivot="macos"

1. Kliknij menu **Visual Studio dla komputerów Mac > Sprawdź aktualizacje...,** aby otworzyć **okno Visual Studio Aktualizacji.**
2. Jeśli jest dostępna aktualizacja, kliknij przycisk **Zainstaluj.**

:::zone-end

## <a name="configure-unity-to-use-visual-studio"></a>Konfigurowanie aparatu Unity do używania Visual Studio

Domyślnie aparatu Unity należy już skonfigurować do używania Visual Studio lub Visual Studio dla komputerów Mac jako edytora skryptów. Możesz to potwierdzić lub zmienić zewnętrzny edytor skryptów na określoną wersję Visual Studio edytorze aparatu Unity.

:::zone pivot="windows"

1. W edytorze aparatu Unity wybierz menu **> preferencje.**
2. Wybierz **kartę Narzędzia zewnętrzne** po lewej stronie.
3. Lista **rozwijana Zewnętrzny** edytor skryptów umożliwia wybór różnych instalacji Visual Studio. Możesz również kliknąć pozycję **Przeglądaj...** na liście rozwijanej, aby dodać wersję nieznajdową na liście.

    ![Menu preferencji Narzędzia zewnętrzne w edytorze aparatu Unity w systemie Windows](../media/vs/preferences-external-tools.png)

4. Jeśli **opcja Przeglądaj...** została wybrana, przejdź do katalogu **Common7/IDE** w katalogu instalacyjnym Visual Studio i wybierz **pozycjędevenv.exe**. Następnie kliknij pozycję **Otwórz**.
5. Po Visual Studio na liście **Edytor** skryptów zewnętrznych upewnij się, że **pole** wyboru Dołączanie edytora jest zaznaczone.
6. Zamknij okno **dialogowe** Preferencje, aby zakończyć proces konfiguracji.

:::zone-end
:::zone pivot="macos"

1. W edytorze aparatu Unity wybierz menu **Preferencje > Unity.**
2. Wybierz **kartę Narzędzia zewnętrzne** po lewej stronie.
3. Lista **rozwijana Zewnętrzny** edytor skryptów umożliwia wybór różnych instalacji Visual Studio. Możesz również kliknąć pozycję **Przeglądaj...** na liście rozwijanej, aby dodać wersję nieznajdową na liście.

    ![Menu preferencji Narzędzia zewnętrzne w edytorze aparatu Unity w systemie macOS](../media/vsm/preferences-external-tools.png)

4. Zamknij okno **dialogowe** Preferencje, aby zakończyć proces konfiguracji.

:::zone-end

## <a name="next-steps"></a>Następne kroki

 Aby dowiedzieć się, jak pracować z projektem aparatu Unity i debugować go w programie Visual Studio, odwiedź stronę Using Visual Studio Tools for Unity (Korzystanie [z Visual Studio Tools for Unity).](using-visual-studio-tools-for-unity.md)
