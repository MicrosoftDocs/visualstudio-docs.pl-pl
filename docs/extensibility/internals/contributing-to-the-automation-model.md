---
title: Współtworzenie modelu automatyzacji | Microsoft Docs
description: Dowiedz się, jak współtworzyć model automatyzacji programu Visual Studio, postępując zgodnie z zestawem wytycznych podczas projektowania pakietu VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 38ea8d477b377f78f5c836ec4661989cdbf8999c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884614"
---
# <a name="contribute-to-the-automation-model"></a>Współtworzenie modelu automatyzacji
Program Visual Studio udostępnia zestaw interfejsów automatyzacji umożliwiających dostosowanie środowiska. Model automatyzacji to model obiektów, który umożliwia użytkownikom końcowym Tworzenie dodatków i rozszerzeń programu Visual Studio.

 Ponadto jest to odpowiednie dla Ciebie, jako programista pakietu VSPackage, aby współtworzyć model automatyzacji; Dzięki temu użytkownicy końcowi pakietu VSPackage mogą tworzyć dodatki i ogólnie zapewniać spójny model użytkownika w przypadku korzystania z pakietu VSPackage w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Aby zapewnić spójność środowiska użytkownika końcowego, można przestrzegać zestawu wytycznych podczas projektowania pakietu VSPackage, tak aby model automatyzacji dla pakietu VSPackage był zgodny z pomysłami w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>W tej sekcji
- [Omówienie modelu automatyzacji](../../extensibility/internals/automation-model-overview.md)

 Definiuje model automatyzacji jako powiązane grupy obiektów kontrolujących główne aspekty wspólnego środowiska. Ten zestaw obiektów jest przedstawiany na diagramie modelu automatyzacji.

- [Zapewnianie automatyzacji dla pakietów VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md)

 W tym artykule omówiono dwa podstawowe sposoby zapewnienia automatyzacji pakietu VSPackage.

- [Uwidacznianie obiektów projektu](../../extensibility/internals/exposing-project-objects.md)

 Zawiera instrukcje krok po kroku dotyczące tworzenia obiektów specyficznych dla pakietu VSPackage.

- [Modelowanie projektu](../../extensibility/internals/project-modeling.md)

 Wyjaśnia standardowe obiekty projektu, które są wymagane do utworzenia automatyzacji dla nowego typu projektu i ilustruje ścieżkę, która jest następująca dla usługi Project Automation. Ten temat zawiera również listę deklaracji i implementacji dla klas.

- [Uwidaczniaj zdarzenia](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Zawiera instrukcje krok po kroku dotyczące tworzenia zdarzeń dla modelu automatyzacji.

- [Obsługa automatyzacji dla stron opcji](../../extensibility/internals/automation-support-for-options-pages.md)

 Opisuje, jak zwrócić obiekt automatyzacji w celu obsługi właściwości okna dialogowego **opcji** niestandardowych pakietu VSPackage w menu **Narzędzia** przez rozszerzenie `DTE.Properties` obiektu.

- [Dostarcz automatyzację kodu](../../extensibility/internals/providing-automation-for-code.md)

 Wyjaśniono, że tworzenie modelu automatyzacji dla kodu nie jest wymagane. Jednak w tym temacie znajduje się link umożliwiający uzyskiwanie szczegółowych informacji do modeli kodu.

- [Instrukcje: zapewnianie automatyzacji dla systemu Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Wyjaśniono, że dostarczanie automatyzacji jest dobrym pomysłem, jeśli chcesz, aby obiekty automatyzacji były dostępne w oknie, a środowisko nie udostępnia jeszcze gotowego obiektu automatyzacji. Omawia automatyzację dla okien narzędzi i okien dokumentów.

- [Korzystanie z modelu automatyzacji](../../extensibility/internals/using-the-automation-model.md)

 Program udostępnia dwa przykłady kodu, które pokazują, jak konsument automatyzacji uzyskuje początkowe obiekty automatyzacji projektu.

- [Automatyzacja dla obiektów Configuration i SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Zawiera informacje o automatyzacji dla obiektów Configuration i SelectedItems.

## <a name="reference"></a>Dokumentacja
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Zawiera przykładowy kod, który pokazuje, jak pakietu VSPackage uczestniczy w modelu obiektów automatyzacji DTE. Wyświetla listę parametrów, wartości zwracane i wybrane uwagi.
