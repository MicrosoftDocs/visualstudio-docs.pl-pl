---
title: Wprowadzenie z Visual Studio Tools for Unity | Microsoft Docs
description: Dowiedz się, jak zainstalować i skonfigurować program Visual Studio do tworzenia aplikacji dla aparatu Unity.
ms.custom: ''
ms.date: 07/13/2020
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
ms.openlocfilehash: 1f8cbe1629aab6a177a46888fe25cf8e3565d91d
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903756"
---
# <a name="get-started-with-visual-studio-and-unity"></a>Wprowadzenie do programu Visual Studio i aparatu Unity

> [!NOTE]
> W tym przewodniku przyjęto założenie, że masz już zainstalowany aparat Unity przy użyciu programu Unity Hub. Jeśli dopiero zaczynasz korzystanie z aparatu Unity, zalecamy odwiedzenie aparatu Unity i przeprowadzenie pierwszej [wprowadzenie z samouczkiem aparatu Unity](https://learn.unity.com/course/getting-started-with-unity) .

## <a name="install-unity-support-for-visual-studio"></a>Zainstaluj obsługę aparatu Unity dla programu Visual Studio

Visual Studio Tools for Unity to bezpłatne rozszerzenie, które zapewnia obsługę pisania i debugowania języka C# i nie tylko. Zapoznaj się z [omówieniem narzędzi dla aparatu Unity](./visual-studio-tools-for-unity.md) , aby uzyskać pełną listę rozszerzeń, które zawiera.

:::zone pivot="windows"

> [!NOTE]
> Ten przewodnik instalacji dotyczy programu Visual Studio. Jeśli używasz Visual Studio Code, odwiedź stronę [projektowania środowiska Unity przy użyciu vs Code dokumentacji](https://code.visualstudio.com/docs/other/unity).

1. [Pobierz instalatora programu Visual Studio](/visualstudio/docs/install/install-visual-studio.md)lub uruchom go, jeśli jest już zainstalowany.
2. Kliknij przycisk **Modyfikuj** (jeśli jest już zainstalowany) lub **Zainstaluj** (w przypadku nowych instalacji) dla żądanej wersji programu Visual Studio.
3. Na karcie **obciążenia** przejdź do sekcji **gry** i wybierz pozycję **Programowanie gier z użyciem obciążenia aparatu Unity** .

    ![Programowanie gier za pomocą aparatu Unity w instalatorze](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> Ten przewodnik instalacji dotyczy Visual Studio dla komputerów Mac. Jeśli używasz Visual Studio Code, odwiedź stronę [projektowania środowiska Unity przy użyciu vs Code dokumentacji](https://code.visualstudio.com/docs/other/unity).

Narzędzia dla aparatu Unity są dołączone do instalacji Visual Studio dla komputerów Mac i nie są wymagane żadne oddzielne kroki instalacji. Można to sprawdzić w **Visual Studio dla komputerów Mac rozszerzenia > > Programowanie gier** . Należy włączyć **Visual Studio dla komputerów Mac narzędzia dla aparatu Unity** .

![Widok Menedżera rozszerzeń z włączonymi narzędziami Visual Studio dla komputerów Mac dla aparatu Unity](../media/vsm/unity-workload.png)

:::zone-end

## <a name="check-for-updates"></a>Sprawdź aktualizacje

Zalecane jest pozostawienie zaktualizowanego programu Visual Studio i Visual Studio dla komputerów Mac, aby były dostępne najnowsze poprawki, funkcje i wsparcie dla aparatu Unity. Nie wymaga to aktualizacji wersji aparatu Unity.

:::zone pivot="windows"

1. Kliknij menu **pomoc > Sprawdź dostępność aktualizacji** .

    ![Menu Sprawdź dostępność aktualizacji w programie Visual Studio 2019](../media/vs/check-for-updates.png)

2. Jeśli dostępna jest aktualizacja, zostanie wyświetlona nowa wersja Instalator programu Visual Studio. Kliknij przycisk **Aktualizuj** .

:::zone-end
:::zone pivot="macos"

1. Kliknij polecenie **Visual Studio dla komputerów Mac > Sprawdź, czy są aktualizacje...** , aby otworzyć okno dialogowe **aktualizacji programu Visual Studio** .
2. Jeśli dostępna jest aktualizacja, kliknij przycisk **Instaluj** .

:::zone-end

## <a name="configure-unity-to-use-visual-studio"></a>Konfigurowanie aparatu Unity do korzystania z programu Visual Studio

Domyślnie aparat Unity powinien już być skonfigurowany do korzystania z programu Visual Studio lub Visual Studio dla komputerów Mac jako Edytor skryptów. Możesz to potwierdzić lub zmienić zewnętrzny edytor skryptów na określoną wersję programu Visual Studio z edytora Unity.

:::zone pivot="windows"

1. W edytorze aparatu Unity wybierz menu **Edytuj preferencje >** .
2. Wybierz kartę **narzędzia zewnętrzne** po lewej stronie.
3. Lista rozwijana **zewnętrzny edytor skryptów** umożliwia wybór różnych instalacji programu Visual Studio. Możesz również kliknąć przycisk **Przeglądaj...** na liście rozwijanej, aby dodać niewyświetlaną wersję.

    ![Menu Preferencje narzędzi zewnętrznych w edytorze aparatu Unity w systemie Windows](../media/vs/preferences-external-tools.png)

4. Jeśli wybrano opcję **Przeglądaj...** , przejdź do katalogu **Common7/IDE** w katalogu instalacyjnym programu Visual Studio i wybierz pozycję **devenv.exe**. Następnie kliknij przycisk **Otwórz**.
5. Po wybraniu programu Visual Studio na liście **zewnętrznych edytorów skryptów** upewnij się, że pole wyboru **dołączanie edytora** jest zaznaczone.
6. Zamknij okno dialogowe **Preferencje** , aby zakończyć proces konfiguracji.

:::zone-end
:::zone pivot="macos"

1. W edytorze Unity wybierz menu **preferencji > Unity** .
2. Wybierz kartę **narzędzia zewnętrzne** po lewej stronie.
3. Lista rozwijana **zewnętrzny edytor skryptów** umożliwia wybór różnych instalacji programu Visual Studio. Możesz również kliknąć przycisk **Przeglądaj...** na liście rozwijanej, aby dodać niewyświetlaną wersję.

    ![Menu Preferencje narzędzi zewnętrznych w edytorze aparatu Unity w systemie macOS](../media/vsm/preferences-external-tools.png)

4. Zamknij okno dialogowe **Preferencje** , aby zakończyć proces konfiguracji.

:::zone-end

## <a name="next-steps"></a>Następne kroki

 Aby dowiedzieć się, jak korzystać z i debugować projekt Unity w programie Visual Studio, odwiedź stronę [przy użyciu Visual Studio Tools for Unity](using-visual-studio-tools-for-unity.md).
