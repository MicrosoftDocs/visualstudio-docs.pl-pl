---
title: Współtworzenie modelu automatyzacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53a669ed6f1ddaa9c2274371439828da24b92789
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726976"
---
# <a name="contributing-to-the-automation-model"></a>Współtworzenie modelu automatyzacji
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Program Visual Studio zapewnia zestaw interfejsów automatyzacji do dostosowywania środowiska. Model automatyzacji to model obiektów, który umożliwia użytkownikom końcowym Tworzenie dodatków programu Visual Studio i rozszerzenia.  
  
 Ponadto jest odpowiednie, jako deweloperów pakietu VSPackage, Współtworzenie modelu automatyzacji; Dzięki temu możesz użytkownikom końcowym z Twojego pakietu VSPackage do tworzenia dodatków i zwykle zapewniają spójny model interfejs użytkownika, korzystając z pakietu VSPackage w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Aby środowisko użytkownika końcowego spójne, możesz wykonać zestaw wytycznych w podczas projektowania usługi pakietu VSPackage, dzięki czemu model automatyzacji do Twojego pakietu VSPackage następuje pomysły w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie modelu automatyzacji](../../extensibility/internals/automation-model-overview.md)  
 Definiuje model automatyzacji jako powiązane grupy obiektów, które kontrolują główne aspekty wspólnego środowiska. Ten zbiór obiektów jest przedstawiony na diagramie modelu automatyzacji.  
  
 [Zapewnianie automatyzacji pakietów VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md)  
 W tym artykule omówiono dwa podstawowe sposoby zapewnianie automatyzacji dla Twojego pakietu VSPackage.  
  
 [Udostępnianie obiektów projektu](../../extensibility/internals/exposing-project-objects.md)  
 Instrukcje krok po kroku do tworzenia obiektów specyficznych dla pakietu VSPackage.  
  
 [Modelowanie projektu](../../extensibility/internals/project-modeling.md)  
 Wyjaśnia obiektów standardowy projekt, które są wymagane do utworzenia automatyzacji nowego typu projektu i przedstawia ścieżką, która następuje po automatyzacji projektu. Ten temat zawiera także listy deklaracji i implementację klasy.  
  
 [Udostępnianie zdarzeń](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Instrukcje krok po kroku dotyczące tworzenia zdarzeń związanych z modelu automatyzacji.  
  
 [Obsługa automatyzacji dla stron opcji](../../extensibility/internals/automation-support-for-options-pages.md)  
 W tym artykule opisano sposób zwracania obiekt automatyzacji dla niestandardowej obsługi właściwości pakietu VSPackage **opcje** okno dialogowe na **narzędzie** menu, rozszerzając `DTE.Properties` obiektu.  
  
 [Zapewnianie automatyzacji kodu](../../extensibility/internals/providing-automation-for-code.md)  
 Wyjaśniono, że tworzenie automatyzacji modelu kodu nie jest wymagane. Jednak łącze znajduje się w tym temacie, zapewniająca wnikliwe informacje do modele kodu.  
  
 [Instrukcje: zapewnianie automatyzacji dla systemu Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Wyjaśniono, że zapewnianie automatyzacji dobrym pomysłem jest zawsze wtedy, gdy chcesz udostępnić obiektów automatyzacji w oknie, a środowisko nie zawiera już obiekt automatyzacji gotowych do użycia. W tym artykule omówiono automatyzacji dla okien narzędzi i oknami dokumentu.  
  
 [Korzystanie z modelu automatyzacji](../../extensibility/internals/using-the-automation-model.md)  
 Zawiera dwa przykłady kodu, które pokazują, jak konsumenta automatyzacji uzyskuje początkowego projektu obiektów automatyzacji.  
  
 [Automatyzacja konfiguracji i obiektów SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Zawiera informacje dotyczące automatyzacji dla opcji konfiguracji i automatyzacja wybrane elementy.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Zawiera przykładowy kod, który pokazuje, jak pakietu VSPackage uczestniczy w DTE modelu obiektowego automatyzacji. Wyświetla listę parametrów, wartości zwracane i wybrane uwagi.  
  
## <a name="related-sections"></a>Sekcje pokrewne

