---
title: Rozwiązywanie problemów z rozszerzeniami dla diagramów warstw | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: troubleshooting
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dd4560673259373b68b370e73a43de424fb7bdb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658476"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>Rozwiązywanie problemów z rozszerzeniami dla diagramów warstw
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten temat dotyczy niektórych problemów, które mogą wystąpić podczas tworzenia rozszerzeń modelu warstwy.

#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-vsprvs"></a>Po naciśnięciu klawisza F5 w celu debugowania mojego rozszerzenia moje polecenia, programy obsługi gestów, rozszerzenia walidacji lub właściwości niestandardowe nie są wyświetlane na diagramach warstwowych w eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

1. Otwórz rozwiązanie rozszerzenia w eksperymentalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , a następnie w menu **kompilacja** kliknij polecenie **Skompiluj ponownie rozwiązanie**.

2. Naciśnij klawisz **F5** lub **Ctrl + F5** , aby uruchomić eksperymentalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Otwórz diagram warstwy i przetestuj rozszerzenie.

   Jeśli to konieczne, przejdź do następnej procedury.

#### <a name="an-old-version-of-my-extension-runs"></a>Zostanie uruchomiona stara wersja mojego rozszerzenia.

1. Upewnij się, że żadne wystąpienie eksperymentalne nie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest uruchomione.

2. Usuń następujący folder:%LocalAppData%\Microsoft\VisualStudio \\ [wersja] \ComponentModelCache

   > [!NOTE]
   > % LocalAppData% jest zazwyczaj *dysk*: \Users \\ *nazwa_użytkownika*\AppData\Local.

   Jeśli to konieczne, przejdź do następnej procedury.

#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Zostanie wyświetlona stara wersja wyników walidacji lub metoda weryfikacji nie została wywołana.

1. W eksperymentalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w menu **kompilacja** kliknij pozycję **czyste rozwiązanie**. Czyści to buforowane wyniki poprzedniej analizy walidacji.

2. Upewnij się, że warstwy w modelu są skojarzone z elementami kodu i że w modelu istnieje co najmniej jedno łącze zależności. Walidacja nie jest wywoływana, jeśli nie ma niczego do zweryfikowania.

3. Zwykłe punkty przerwania mogą nie działać w metodzie walidacji, ponieważ są uruchamiane w osobnym procesie. Musisz wstawić wywołanie do, `System.Diagnostics.Debugger.Launch()` Jeśli chcesz przejść przez metodę.

4. W polu **source. Extension. vsixmanifest** w projekcie walidacji warstwy upewnij się, że dodano zarówno element **składnika MEF** , jak i **niestandardowy element typu rozszerzenia** w obszarze **zawartość**.

## <a name="see-also"></a>Zobacz też
 [Rozszerzone diagramy warstw](../modeling/extend-layer-diagrams.md)
