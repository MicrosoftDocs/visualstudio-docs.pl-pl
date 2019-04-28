---
title: Rozwiązywanie problemów z rozszerzeniami dla diagramów warstw | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: troubleshooting
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 38a459760dd66e1160bd8b197ee9883b617639b2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439750"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>Rozwiązywanie problemów z rozszerzeniami dla diagramów warstw
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie omawia niektóre problemy, które można napotkać podczas tworzenia warstwy modelu rozszerzeń.  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-includevsprvsincludesvsprvs-mdmd"></a>Po naciśnięciu klawisza klawisz F5, aby debugować Moje rozszerzenia, polecenia, programy obsługi gestu, rozszerzenia sprawdzania poprawności lub właściwości niestandardowe nie są wyświetlane na diagramach warstwy w doświadczalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
1. Otwórz swoje rozwiązanie rozszerzenia w doświadczalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], a następnie na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
2. Naciśnij klawisz **F5** lub **kombinację klawiszy CTRL + F5** do uruchom wystąpienie eksperymentalne programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Otwórz diagram warstwy i przetestuj swoje rozszerzenia.  
  
   Przejdź do następnej procedury, jeśli to konieczne.  
  
#### <a name="an-old-version-of-my-extension-runs"></a>Uruchamia starą wersję mojego rozszerzenia.  
  
1. Upewnij się, że żadne wystąpienie doświadczalne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest uruchomiona.  
  
2. Usuń następujący folder: %LocalAppData%\Microsoft\VisualStudio\\\ComponentModelCache [wersja]  
  
   > [!NOTE]
   > % LocalAppData % zazwyczaj znajduje *DriveName*: \Users\\*UserName*\AppData\Local.  
  
   Przejdź do następnej procedury, jeśli to konieczne.  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Pojawi się stara wersja mojego wyniku weryfikacji lub Moja metoda sprawdzania poprawności nie jest wywoływana.  
  
1. W doświadczalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]na **kompilacji** menu, kliknij przycisk **czyste rozwiązanie**. Czyści buforowane wyników poprzedniej analizy sprawdzania poprawności.  
  
2. Upewnij się, że warstwy w modelu są skojarzone z elementami kodu i że istnieje co najmniej jedno łącze zależności w modelu. Sprawdzanie poprawności nie jest wywoływana, jeśli nie ma nic do sprawdzania poprawności.  
  
3. Regularne punkty przerwania mogą nie działać w metodzie sprawdzania poprawności, ponieważ jest uruchamiana w oddzielnym procesie. Należy wstawić wywołanie `System.Diagnostics.Debugger.Launch()` Jeśli chcesz przejść przez metodę.  
  
4. W **source.extension.vsixmanifest** upewnij się, że dodano zarówno w projekcie sprawdzania poprawności warstwy **składnik MEF** elementu i **niestandardowy typ rozszerzenia** w obszarze **Zawartości**.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzone diagramy warstw](../modeling/extend-layer-diagrams.md)
