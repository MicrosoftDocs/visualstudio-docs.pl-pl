---
title: Wprowadzenie do programu Visual Studio Tools for Unity | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302274"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Wprowadzenie do programu Visual Studio Tools for Unity

## <a name="install-visual-studio"></a>Instalacja programu Visual Studio

### <a name="unity-bundled-installation"></a>Instalacja w pakiecie Unity

Począwszy od Unity 2018.1, Visual Studio jest domyślnym edytorem skryptów języka C# dla Unity i znajduje się w Unity Download Assistant, a także w narzędziu instalacyjnym Unity Hub.

- Pobierz Unity z [store.unity.com](https://store.unity.com/).

Podczas instalacji upewnij się, że visual studio jest sprawdzany na liście składników do zainstalowania w unity:

#### <a name="unity-hub"></a>Centrum Jedności

![instalacja koncentratora unity](media/vstu_unity-hub.png)

#### <a name="unity-download-assistant"></a>Asystent pobierania Unity

![instalacja asystenta pobierania unity](media/vstu_download-assistant.png)

#### <a name="check-for-updates-to-visual-studio"></a>Sprawdzanie dostępności aktualizacji programu Visual Studio

Wersja programu Visual Studio dołączone do instalacji Unity może nie być najnowsza. Zaleca się sprawdzanie dostępności aktualizacji, aby upewnić się, że masz dostęp do najnowszych narzędzi i funkcji.

- [Aktualizowanie programu Visual Studio](../install/update-visual-studio.md)

### <a name="manual-installation"></a>Instalacja ręczna

Jeśli masz już zainstalowany program Visual Studio 2017 lub wolisz zainstalować ręcznie, uruchom instalator programu Visual Studio.

1. [Pobierz instalator programu Visual Studio](../install/install-visual-studio.md)lub otwórz go, jeśli jest już zainstalowany.

1. Kliknij **pozycję Modyfikuj** (jeśli jest już zainstalowana) lub **Zainstaluj** (dla nowych instalacji) dla żądanej wersji programu Visual Studio.

1. Na karcie **Obciążenia** przewiń do sekcji **Mobile & Gaming** i wybierz program tworzenia gier z obciążeniem **Unity.**

    ![Obciążenie związane z jednością](media/vstu_unity-workload.png)

1. Kliknij **pozycję Modyfikuj** (jeśli jest już zainstalowana) lub **Zainstaluj** (dla nowych instalacji) w prawym dolnym rogu okna instalatora.

## <a name="configure-unity-for-use-with-visual-studio"></a>Konfigurowanie unity do użytku z programem Visual Studio

Począwszy od Unity 2018.1, Visual Studio powinien być domyślny edytor skryptów zewnętrznych w Unity. Można to potwierdzić lub zmienić zewnętrzny edytor skryptów na określoną wersję programu Visual Studio:

1. Wybierz **preferencje** z menu **Edycja.**

   ![Wybierz preferencje](media/vstu_unity-preferences.png)

2. W oknie dialogowym Preferencje wybierz kartę **Narzędzia zewnętrzne.**

3. Z listy rozwijanej **Edytor skryptów zewnętrznych** wybierz żądaną wersję programu Visual Studio, jeśli jest na liście, w przeciwnym razie wybierz **pozycję Przeglądaj...**.

   ![Wybierz program Visual Studio](media/vstu_unity-external-tools.png)

4. Jeśli wybrano **opcję Przeglądaj...** przejdź do katalogu **Common7/IDE** w katalogu instalacyjnym programu Visual Studio i wybierz program **devenv.exe**. Następnie kliknij przycisk **Otwórz**.

   ![Wybierz otwórz](media/vstu_browse-for-application.png)

5. Po wybraniu programu Visual Studio na liście **Edytor skryptów zewnętrznych** upewnij się, że jest zaznaczone pole wyboru **Dołączanie edytora.**

6. Zamknij okno dialogowe **Preferencje,** aby zakończyć proces konfiguracji.

## <a name="support-for-older-versions"></a>Obsługa starszych wersji

 Pobierz i zainstaluj narzędzia programu Visual Studio dla unity z portalu Visual Studio Marketplace. Musisz zainstalować odpowiedni pakiet dla swojej wersji programu Visual Studio.

- Dla społeczności programu Visual Studio 2015, programu Visual Studio 2015 Professional lub Visual Studio 2015 Enterprise:

   [Pobierz narzędzia programu Visual Studio 2015 dla unity](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Narzędzia programu Visual Studio dla unity wymaga Unity 5.2 i powyżej, a także wersji programu Visual Studio, która obsługuje rozszerzenia, takie jak Visual Studio Community, Professional, Premium lub Enterprise. Aby sprawdzić, czy narzędzia programu Visual Studio dla unity są włączone w instalacji Unity, wybierz o **jedności** z menu **Pomoc** i poszukaj tekstu "Microsoft Visual Studio Tools for Unity enabled" w lewym dolnym rogu okna dialogowego.
> ![o Jedności](media/vstu_about-unity.png)

## <a name="next-steps"></a>Następne kroki

 Aby dowiedzieć się, jak pracować z projektem Unity i debugować go w programie Visual Studio, zobacz [Narzędzia programu Visual Studio dla unity.](../cross-platform/using-visual-studio-tools-for-unity.md)
