---
title: Wprowadzenie do narzędzi Visual Studio Tools for Unity | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: c22b9c25f95ea26f2cdaf5c2035fb7a373123241
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684785"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Rozpoczynanie pracy z usługą Visual Studio Tools for Unity

## <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

### <a name="unity-bundled-installation"></a>Instalacja aparatu Unity powiązane

Począwszy od Unity 2018.1, Visual Studio jest domyślnego języka C# skrypt edytora dla aparatu Unity i znajduje się w Unity Pobierz Asystenta ustawień, a także narzędzie instalacji Centrum aparatu Unity.

- Pobierz oprogramowanie Unity z [store.unity.com](https://store.unity.com/).

Podczas instalacji upewnij się, że zaznaczono Visual Studio, na liście składników do zainstalowania przy użyciu aparatu Unity:

#### <a name="unity-hub"></a>Centrum platformy Unity

![Instalacja Centrum aparatu Unity](media/vstu_unity-hub.png)

#### <a name="unity-download-assistant"></a>Asystent pobieranie aparatu Unity

![Instalacja Asystenta pobieranie aparatu Unity](media/vstu_download-assistant.png)

#### <a name="check-for-updates-to-visual-studio"></a>Sprawdź, czy są dostępne aktualizacje programu Visual Studio

Wersja programu Visual Studio, dołączone do instalacji programu Unity może być r. Zalecane jest, aby sprawdzał dostępność aktualizacji upewnić się, że masz dostęp do najnowszych narzędzi i funkcji.

- [Aktualizowanie programu Visual Studio](../install/update-visual-studio.md)

### <a name="manual-installation"></a>Instalacja ręczna

Jeśli już masz zainstalowanego programu Visual Studio 2017 lub chcesz ręcznie zainstalować, uruchom Instalatora programu Visual Studio.

1. [Pobierz Instalatora programu Visual Studio](../install/install-visual-studio.md), lub otworzyć go, jeśli już zainstalowane.

1. Kliknij przycisk **Modyfikuj** (jeśli jest już zainstalowana) lub **zainstalować** (w przypadku nowych instalacji) dla odpowiednią wersję programu Visual Studio.

1. Na **obciążeń** karty, przewiń do **urządzenia przenośne i gry** i wybierz pozycję **gier z użyciem aparatu Unity** obciążenia.

    ![Obciążeniem aparatu Unity](media/vstu_unity-workload.png)

1. Kliknij przycisk **Modyfikuj** (jeśli jest już zainstalowana) lub **zainstalować** (w przypadku nowych instalacji) w prawym dolnym rogu okna Instalatora.

## <a name="configure-unity-for-use-with-visual-studio"></a>Konfigurowanie aparatu Unity do użycia z programem Visual Studio

Począwszy od Unity 2018.1, Visual Studio powinien być domyślnego edytora skryptu zewnętrznego na platformie Unity. Można to potwierdzić lub zmienić edytor skryptu zewnętrznego do określonej wersji programu Visual Studio:

1. Wybierz **preferencje** z **Edytuj** menu.

   ![Wybierz polecenie Preferencje](media/vstu_unity-preferences.png)

2. W oknie dialogowym Preferencje wybierz **zewnętrznych narzędzi** kartę.

3. Z **Edytor skryptów zewnętrznych** listy rozwijanej wybierz odpowiednią wersję programu Visual Studio, jeśli ta opcja jest wyświetlana, w przeciwnym razie wybierz **Przeglądaj...** .

   ![Wybierz program Visual Studio](media/vstu_unity-external-tools.png)

4. Jeśli **Przeglądaj...**  została zaznaczona, przejdź do **Common7/IDE** katalog wewnątrz usługi katalogu instalacyjnego programu Visual Studio i wybierz pozycję **devenv.exe**. Następnie kliknij przycisk **Otwórz**.

   ![Wybierz przycisk Otwórz](media/vstu_browse-for-application.png)

5. Po wybraniu w programie Visual Studio **Edytor skryptów zewnętrznych** listy, upewnij się, że **dołączanie edytora** pole wyboru jest zaznaczone.

6. Zamknij **preferencje** okno dialogowe, aby zakończyć proces konfiguracji.

## <a name="support-for-older-versions"></a>Obsługa starszych wersji

 Pobierz i zainstaluj program Visual Studio Tools for Unity z witryny Marketplace programu Visual Studio. Musisz zainstalować odpowiedni pakiet dla używanej wersji programu Visual Studio.

- For Visual Studio 2015 Community, Visual Studio 2015 Professional, or Visual Studio 2015 Enterprise:

   [Pobierz program Visual Studio 2015 Tools for Unity](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Visual Studio Tools for Unity wymaga Unity 5.2 i powyżej, a także wersji programu Visual Studio, która obsługuje rozszerzeń, takich jak program Visual Studio Community, Professional, Premium lub Enterprise. Aby sprawdzić, czy program Visual Studio Tools for Unity są włączone w instalacji programu Unity, wybierz **o Unity** z **pomocy** menu i zwróć uwagę na tekst "Microsoft Visual Studio Tools for Unity włączona" w lewym dolnym rogu okna dialogowego.
> ![Unity — informacje](media/vstu_about-unity.png)

## <a name="next-steps"></a>Następne kroki

 Aby dowiedzieć się, jak pracować z i debugowanie projektu środowiska Unity w programie Visual Studio, zobacz [Visual Studio Tools for Unity](../cross-platform/using-visual-studio-tools-for-unity.md).
