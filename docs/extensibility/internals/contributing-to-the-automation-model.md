---
title: Współtworzenie modelu automatyzacji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d660edc740229c3e91b99e1f59eb37b4e9312098
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709267"
---
# <a name="contribute-to-the-automation-model"></a>Współtworzenie modelu automatyzacji
Visual Studio udostępnia zestaw interfejsów automatyzacji do dostosowywania środowiska. Model automatyzacji jest modelem obiektowym, który umożliwia użytkownikom końcowym tworzenie dodatków i rozszerzeń programu Visual Studio.

 Ponadto jest odpowiedni dla Ciebie, jako deweloper VSPackage, aby przyczynić się do modelu automatyzacji; w ten sposób można włączyć użytkowników końcowych vsPackage do tworzenia dodatków i ogólnie zapewniają spójne środowisko [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]modelu użytkownika, gdy używają vsPackage w .

 Aby środowisko użytkownika końcowego było spójne, można postępować zgodnie z zestawem wytycznych podczas projektowania vspackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]tak, aby model automatyzacji dla vspackage postępował zgodnie z pomysłami w programie .

## <a name="in-this-section"></a>W tej sekcji
- [Omówienie modelu automatyzacji](../../extensibility/internals/automation-model-overview.md)

 Definiuje model automatyzacji jako powiązane grupy obiektów, które kontrolują główne aspekty wspólnego środowiska. Ten zestaw obiektów jest na zdjęciu na diagramie modelu automatyzacji.

- [Zapewnij automatyzację vspackages](../../extensibility/internals/providing-automation-for-vspackages.md)

 W tym artykule omówiono dwa główne sposoby zapewnienia automatyzacji dla vspackage.

- [Udostępnianie obiektów projektu](../../extensibility/internals/exposing-project-objects.md)

 Zawiera instrukcje krok po kroku dotyczące tworzenia obiektów specyficznych dla vspackage.

- [Modelowanie projektu](../../extensibility/internals/project-modeling.md)

 W tym artykule wyjaśniono standardowe obiekty projektu, które są wymagane do tworzenia automatyzacji dla nowego typu projektu i ilustruje ścieżkę, którą podąża automatyzacja projektu. Ten temat zawiera również listę deklaracji i implementacji dla klas.

- [Ujawnianie zdarzeń](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Zawiera instrukcje krok po kroku dotyczące tworzenia zdarzeń dla modelu automatyzacji.

- [Obsługa automatyzacji stron opcji](../../extensibility/internals/automation-support-for-options-pages.md)

 W tym artykule opisano sposób zwracania obiektu automatyzacji do **Options** obsługi właściwości okna dialogowego Opcje `DTE.Properties` niestandardowe VSPackage w menu **Narzędzia** przez rozszerzenie obiektu.

- [Zapewnij automatyzację kodu](../../extensibility/internals/providing-automation-for-code.md)

 W tym artykule wyjaśniono, że tworzenie modelu automatyzacji dla kodu nie jest wymagane. Jednak łącze znajduje się w tym temacie, który zawiera wnikliwe informacje do modeli kodu.

- [Jak: Zapewnienie automatyzacji dla systemu Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 W tym artykule wyjaśniono, że zapewnienie automatyzacji jest dobrym pomysłem, gdy chcesz udostępnić obiekty automatyzacji w oknie, a środowisko nie zapewnia już gotowego obiektu automatyzacji. W tym artykule omówiono automatyzację okien narzędzi i okien dokumentów.

- [Korzystanie z modelu automatyzacji](../../extensibility/internals/using-the-automation-model.md)

 Zawiera dwa przykłady kodu, które pokazują, jak konsument automatyzacji uzyskuje początkowe obiekty automatyzacji projektu.

- [Automatyzacja dla obiektów konfiguracji i selecteditem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Zawiera informacje o automatyzacji dla konfiguracji i SelectedItems obiektów.

## <a name="reference"></a>Tematy pomocy
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>Zawiera przykładowy kod, który pokazuje, jak VSPackage uczestniczy w modelu obiektów automatyzacji DTE. Wyświetla listę parametrów, zwracanych wartości i wybranych uwag.
