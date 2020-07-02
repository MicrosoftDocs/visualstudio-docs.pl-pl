---
title: Wprowadzenie z Visual Studio Tools for Unity | Microsoft Docs
ms.custom: ''
ms.date: 05/11/2020
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: indiesaudi
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 32766fdf69136f3882186bbcad08aaf83d2e573e
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815750"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Wprowadzenie do Visual Studio Tools for Unity

## <a name="install-visual-studio"></a>Instalowanie programu Visual Studio

### <a name="unity-bundled-installation"></a>Instalacja z pakietem Unity

Począwszy od aparatu Unity 2018,1, program Visual Studio jest domyślnym edytorem skryptów języka C# dla aparatu Unity i jest zawarty w Asystencie pobierania aparatu Unity, a także narzędzia instalacji centrum Unity.

- Pobierz aparat Unity z [Store.Unity.com](https://store.unity.com/).

Podczas instalacji upewnij się, że program Visual Studio został zaewidencjonowany na liście składników do zainstalowania przy użyciu aparatu Unity:

#### <a name="unity-hub"></a>Centrum Unity

:::moniker range="vs-2017"
![Instalacja centrum Unity](media/vs-2017/vstu-unity-hub.png)
:::moniker-end
:::moniker range=">=vs-2019"
![Instalacja centrum Unity](media/vs-2019/vstu-unity-hub.png)
:::moniker-end

:::moniker range="vs-2017"

#### <a name="unity-download-assistant"></a>Asystent pobierania aparatu Unity

![instalacja Asystenta pobierania aparatu Unity](media/vs-2017/vstu-download-assistant.png)

Wersja programu Visual Studio dołączona do instalacji aparatu Unity może nie być najnowsza. Jeśli zostanie wyświetlony monit o zainstalowanie programu Visual Studio 2017, zalecamy ręczne zainstalowanie nowszej wersji programu Visual Studio.
:::moniker-end

### <a name="manual-installation"></a>Instalacja ręczna

Jeśli masz już zainstalowany program Visual Studio lub wolisz przeprowadzić ręczną instalację, uruchom Instalatora programu Visual Studio.

1. [Pobierz instalatora programu Visual Studio](../install/install-visual-studio.md)lub Otwórz go, jeśli jest już zainstalowany.

1. Kliknij przycisk **Modyfikuj** (jeśli jest już zainstalowany) lub **Zainstaluj** (w przypadku nowych instalacji) dla żądanej wersji programu Visual Studio.

1. Na karcie **obciążenia** przejdź do sekcji **gier & mobilnych** i wybierz pozycję **Programowanie gier z użyciem obciążenia aparatu Unity** .

   :::moniker range="vs-2017"
   ![Obciążenie aparatu Unity](media/vs-2017/vstu-unity-workload.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Obciążenie aparatu Unity](media/vs-2019/vstu-unity-workload.png)
   :::moniker-end

1. Kliknij przycisk **Modyfikuj** (jeśli jest już zainstalowany) lub **Zainstaluj** (w przypadku nowych instalacji) w prawym dolnym rogu okna Instalatora.


#### <a name="check-for-updates-to-visual-studio"></a>Sprawdź dostępność aktualizacji programu Visual Studio

Zalecane jest sprawdzenie dostępności aktualizacji w programie Visual Studio, aby upewnić się, że masz dostęp do najnowszych narzędzi i funkcji. Nie spowoduje to przerwania projektu środowiska Unity.

- [Aktualizowanie programu Visual Studio](../install/update-visual-studio.md)


## <a name="configure-unity-for-use-with-visual-studio"></a>Konfigurowanie aparatu Unity do użycia z programem Visual Studio

Począwszy od aparatu Unity 2018,1, program Visual Studio powinien być domyślnym zewnętrznym edytorem skryptów w aparacie Unity. Możesz to potwierdzić lub zmienić zewnętrzny edytor skryptów na określoną wersję programu Visual Studio:

1. Wybierz pozycję **Preferencje** z menu **Edycja** .

   :::moniker range="vs-2017"
   ![Wybierz Preferencje](media/vs-2017/vstu-unity-preferences.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Wybierz Preferencje](media/vs-2019/vstu-unity-preferences.png)
   :::moniker-end

2. W oknie dialogowym preferencji wybierz kartę **narzędzia zewnętrzne** .

3. Z listy rozwijanej **zewnętrzny edytor skryptów** wybierz żądaną wersję programu Visual Studio, jeśli jest wyświetlana, w przeciwnym razie wybierz pozycję **Przeglądaj...**.

   :::moniker range="vs-2017"
   ![Wybierz program Visual Studio](media/vs-2017/vstu-unity-external-tools.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Wybierz program Visual Studio](media/vs-2019/vstu-unity-external-tools.png)
   :::moniker-end


4. Jeśli wybrano opcję **Przeglądaj...** , przejdź do katalogu **Common7/IDE** w katalogu instalacyjnym programu Visual Studio i wybierz pozycję **devenv.exe**. Następnie kliknij przycisk **Otwórz**.

   :::moniker range="vs-2017"
   ![Wybierz pozycję Otwórz](media/vs-2017/vstu-browse-for-application.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Wybierz pozycję Otwórz](media/vs-2019/vstu-browse-for-application.png)
   :::moniker-end

5. Po wybraniu programu Visual Studio na liście **zewnętrznych edytorów skryptów** upewnij się, że pole wyboru **dołączanie edytora** jest zaznaczone.

6. Zamknij okno dialogowe **Preferencje** , aby zakończyć proces konfiguracji.

## <a name="support-for-older-versions"></a>Obsługa starszych wersji

Pobierz i zainstaluj Visual Studio Tools for Unity z Visual Studio Marketplace. Musisz zainstalować odpowiedni pakiet dla używanej wersji programu Visual Studio.

- W przypadku programu Visual Studio 2015 Community, Visual Studio 2015 Professional lub Visual Studio 2015 Enterprise:

   [Pobierz narzędzia programu Visual Studio 2015 dla aparatu Unity](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Visual Studio Tools for Unity wymaga aparatu Unity 5,2 i nowszego, a także wersji programu Visual Studio, która obsługuje rozszerzenia, takie jak Visual Studio Community, Professional, Premium lub Enterprise. Aby sprawdzić, czy Visual Studio Tools for Unity są włączone w instalacji aparatu Unity, wybierz pozycję **informacje z aparatu Unity** z menu **Pomoc** i Wyszukaj tekst "Microsoft Visual Studio Tools for Unity Enabled" w lewym dolnym rogu okna dialogowego.
> ![Informacje o aparacie Unity](media/vs-2019/vstu-about-unity.png)


## <a name="next-steps"></a>Następne kroki

 Aby dowiedzieć się, jak korzystać z i debugować projekt Unity w programie Visual Studio, zobacz [Visual Studio Tools for Unity](../cross-platform/using-visual-studio-tools-for-unity.md).
