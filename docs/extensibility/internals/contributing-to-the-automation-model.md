---
title: Współtworzenie modelu automatyzacji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ebe9a3d1c314a8e3b15ae7588f38abfd50518d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910734"
---
# <a name="contribute-to-the-automation-model"></a>Współtworzenie modelu automatyzacji
Program Visual Studio zapewnia zestaw interfejsów automatyzacji do dostosowywania środowiska. Model automatyzacji to model obiektów, który umożliwia użytkownikom końcowym Tworzenie dodatków programu Visual Studio i rozszerzenia.

 Ponadto jest odpowiednie, jako deweloperów pakietu VSPackage, Współtworzenie modelu automatyzacji; Dzięki temu możesz użytkownikom końcowym z Twojego pakietu VSPackage do tworzenia dodatków i zwykle zapewniają spójny model interfejs użytkownika, korzystając z pakietu VSPackage w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Aby środowisko użytkownika końcowego spójne, możesz wykonać zestaw wytycznych w podczas projektowania usługi pakietu VSPackage, dzięki czemu model automatyzacji do Twojego pakietu VSPackage następuje pomysły w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>W tej sekcji
- [Omówienie modelu automatyzacji](../../extensibility/internals/automation-model-overview.md)

 Definiuje model automatyzacji jako powiązane grupy obiektów, które kontrolują główne aspekty wspólnego środowiska. Ten zbiór obiektów jest przedstawiony na diagramie modelu automatyzacji.

- [Zapewnianie automatyzacji pakietów VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md)

 W tym artykule omówiono dwa podstawowe sposoby zapewnianie automatyzacji dla Twojego pakietu VSPackage.

- [Udostępnianie obiektów projektu](../../extensibility/internals/exposing-project-objects.md)

 Instrukcje krok po kroku do tworzenia obiektów specyficznych dla pakietu VSPackage.

- [Modelowanie projektu](../../extensibility/internals/project-modeling.md)

 Wyjaśnia obiektów standardowy projekt, które są wymagane do utworzenia automatyzacji nowego typu projektu i przedstawia ścieżką, która następuje po automatyzacji projektu. Ten temat zawiera także listy deklaracji i implementację klasy.

- [Udostępnianie zdarzeń](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Instrukcje krok po kroku dotyczące tworzenia zdarzeń związanych z modelu automatyzacji.

- [Automatyzacja obsługi dla stron opcji](../../extensibility/internals/automation-support-for-options-pages.md)

 W tym artykule opisano sposób zwracania obiekt automatyzacji dla niestandardowej obsługi właściwości pakietu VSPackage **opcje** okno dialogowe na **narzędzie** menu, rozszerzając `DTE.Properties` obiektu.

- [Zapewnianie automatyzacji kodu](../../extensibility/internals/providing-automation-for-code.md)

 Wyjaśniono, że tworzenie automatyzacji modelu kodu nie jest wymagane. Jednak łącze znajduje się w tym temacie, zapewniająca wnikliwe informacje do modele kodu.

- [Instrukcje: Zapewnianie automatyzacji dla Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Wyjaśniono, że zapewnianie automatyzacji dobrym pomysłem jest zawsze wtedy, gdy chcesz udostępnić obiektów automatyzacji w oknie, a środowisko nie zawiera już obiekt automatyzacji gotowych do użycia. W tym artykule omówiono automatyzacji dla okien narzędzi i oknami dokumentu.

- [Użyj modelu automatyzacji](../../extensibility/internals/using-the-automation-model.md)

 Zawiera dwa przykłady kodu, które pokazują, jak konsumenta automatyzacji uzyskuje początkowego projektu obiektów automatyzacji.

- [Automatyzacja obiektów konfiguracji i SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Zawiera informacje dotyczące automatyzacji konfiguracji i SelectedItems obiektów.

## <a name="reference"></a>Tematy pomocy
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Zawiera przykładowy kod, który pokazuje, jak pakietu VSPackage uczestniczy w DTE modelu obiektowego automatyzacji. Wyświetla listę parametrów, wartości zwracane i wybrane uwagi.
