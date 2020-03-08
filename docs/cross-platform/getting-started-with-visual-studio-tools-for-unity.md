---
title: Wprowadzenie z Visual Studio Tools for Unity | Microsoft Docs
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408791"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Wprowadzenie do Visual Studio Tools for Unity

## <a name="install-visual-studio"></a>Instalacja programu Visual Studio

### <a name="unity-bundled-installation"></a>Instalacja z pakietem Unity

Począwszy od aparatu Unity 2018,1, program Visual Studio jest C# domyślnym edytorem skryptów dla aparatu Unity i jest zawarty w Asystencie pobierania aparatu Unity, a także narzędzia instalacji centrum Unity.

- Pobierz aparat Unity z [Store.Unity.com](https://store.unity.com/).

Podczas instalacji upewnij się, że program Visual Studio został zaewidencjonowany na liście składników do zainstalowania przy użyciu aparatu Unity:

#### <a name="unity-hub"></a>Centrum platformy Unity

![Instalacja Centrum aparatu Unity](media/vstu_unity-hub.png)

#### <a name="unity-download-assistant"></a>Asystent pobieranie aparatu Unity

![Instalacja Asystenta pobieranie aparatu Unity](media/vstu_download-assistant.png)

#### <a name="check-for-updates-to-visual-studio"></a>Sprawdź dostępność aktualizacji programu Visual Studio

Wersja programu Visual Studio dołączona do instalacji aparatu Unity może nie być najnowsza. Zalecane jest, aby sprawdzał dostępność aktualizacji upewnić się, że masz dostęp do najnowszych narzędzi i funkcji.

- [Aktualizowanie programu Visual Studio](../install/update-visual-studio.md)

### <a name="manual-installation"></a>Instalacja ręczna

Jeśli masz już zainstalowany program Visual Studio 2017 lub wolisz przeprowadzić ręczną instalację, uruchom Instalatora programu Visual Studio.

1. [Pobierz instalatora programu Visual Studio](../install/install-visual-studio.md)lub Otwórz go, jeśli jest już zainstalowany.

1. Kliknij przycisk **Modyfikuj** (jeśli jest już zainstalowany) lub **Zainstaluj** (w przypadku nowych instalacji) dla żądanej wersji programu Visual Studio.

1. Na karcie **obciążenia** przejdź do sekcji **gier & mobilnych** i wybierz pozycję **Programowanie gier z użyciem obciążenia aparatu Unity** .

    ![Obciążenie aparatu Unity](media/vstu_unity-workload.png)

1. Kliknij przycisk **Modyfikuj** (jeśli jest już zainstalowany) lub **Zainstaluj** (w przypadku nowych instalacji) w prawym dolnym rogu okna Instalatora.

## <a name="configure-unity-for-use-with-visual-studio"></a>Konfigurowanie aparatu Unity do użycia z programem Visual Studio

Począwszy od Unity 2018.1, Visual Studio powinien być domyślnego edytora skryptu zewnętrznego na platformie Unity. Możesz to potwierdzić lub zmienić zewnętrzny edytor skryptów na określoną wersję programu Visual Studio:

1. Wybierz pozycję **Preferencje** z menu **Edycja** .

   ![Wybierz polecenie Preferencje](media/vstu_unity-preferences.png)

2. W oknie dialogowym preferencji wybierz kartę **narzędzia zewnętrzne** .

3. Z listy rozwijanej **zewnętrzny edytor skryptów** wybierz żądaną wersję programu Visual Studio, jeśli jest wyświetlana, w przeciwnym razie wybierz pozycję **Przeglądaj...** .

   ![Wybierz program Visual Studio](media/vstu_unity-external-tools.png)

4. Jeśli wybrano opcję **Przeglądaj...** , przejdź do katalogu **Common7/IDE** w katalogu instalacyjnym programu Visual Studio i wybierz pozycję **devenv. exe**. Następnie kliknij przycisk **Otwórz**.

   ![Wybierz przycisk Otwórz](media/vstu_browse-for-application.png)

5. Po wybraniu programu Visual Studio na liście **zewnętrznych edytorów skryptów** upewnij się, że pole wyboru **dołączanie edytora** jest zaznaczone.

6. Zamknij okno dialogowe **Preferencje** , aby zakończyć proces konfiguracji.

## <a name="support-for-older-versions"></a>Obsługa starszych wersji

 Pobierz i zainstaluj Visual Studio Tools for Unity z Visual Studio Marketplace. Musisz zainstalować odpowiedni pakiet dla używanej wersji programu Visual Studio.

- For Visual Studio 2015 Community, Visual Studio 2015 Professional, or Visual Studio 2015 Enterprise:

   [Pobierz narzędzia programu Visual Studio 2015 dla aparatu Unity](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Visual Studio Tools for Unity wymaga aparatu Unity 5,2 i nowszego, a także wersji programu Visual Studio, która obsługuje rozszerzenia, takie jak Visual Studio Community, Professional, Premium lub Enterprise. Aby sprawdzić, czy Visual Studio Tools for Unity są włączone w instalacji aparatu Unity, wybierz pozycję **informacje z aparatu Unity** z menu **Pomoc** i Wyszukaj tekst "Microsoft Visual Studio Tools for Unity Enabled" w lewym dolnym rogu okna dialogowego.
> ![na temat](media/vstu_about-unity.png) Unity

## <a name="next-steps"></a>Następne kroki

 Aby dowiedzieć się, jak korzystać z i debugować projekt Unity w programie Visual Studio, zobacz [Visual Studio Tools for Unity](../cross-platform/using-visual-studio-tools-for-unity.md).
