---
title: Podstawowe informacje o integracji kontroli źródła | Microsoft Docs
description: 'Poznaj dwa typy integracji kontroli źródła obsługiwane przez program Visual Studio: wtyczkę kontroli źródła i rozwiązanie kontroli źródła oparte na pakietu VSPackage.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 155e662eae0dda6689a233e31fd62bb72259ae8b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069338"
---
# <a name="source-control-integration-essentials"></a>Podstawowe informacje o integracji kontroli kodu źródłowego
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje dwa typy integracji kontroli źródła: Wtyczka kontroli źródła, która zapewnia podstawowe funkcje i jest tworzona przy użyciu interfejsu API kontroli źródła (dawniej znanego jako interfejs API MSSCCI), oraz rozwiązania integracji kontroli źródła opartego na pakietu VSPackage, które zapewnia bardziej niezawodne funkcje.

## <a name="source-control-plug-in"></a>Wtyczka kontroli źródła
 Wtyczka do kontroli źródła jest zapisywana jako biblioteka DLL, która implementuje interfejs API wtyczki kontroli źródła. Funkcje integracji i kontroli źródła są udostępniane za pomocą interfejsu API. Takie podejście jest łatwiejsze do zaimplementowania niż pakietu VSPackage kontroli źródła i używa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika (UI) w przypadku większości operacji kontroli źródła.

 Aby zaimplementować wtyczkę kontroli źródła przy użyciu interfejsu API wtyczki kontroli źródła, wykonaj następujące kroki:

1. Utwórz bibliotekę DLL, która implementuje funkcje określone w [wtyczkach kontroli źródła](../../extensibility/source-control-plug-ins.md).

2. Zarejestruj bibliotekę DLL, wprowadzając odpowiednie wpisy rejestru zgodnie z opisem w temacie [How to: Install a Source Control plug-in](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).

3. Utwórz interfejs użytkownika pomocnika i Wyświetl go po wyświetleniu monitu przez pakiet adaptera kontroli źródła ( [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] składnik obsługujący funkcje kontroli źródła za pomocą wtyczek kontroli źródła).

   Aby uzyskać więcej informacji, zobacz [tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md).

## <a name="source-control-vspackage"></a>Pakietu VSPackage kontroli źródła
 Implementacja pakietu VSPackage kontroli źródła pozwala opracowywać dostosowaną zamiennik dla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika kontroli źródła. Takie podejście zapewnia pełną kontrolę nad integracją kontroli źródła, ale wymaga podania elementów interfejsu użytkownika i zaimplementowania interfejsów kontroli źródła, które w przeciwnym razie byłyby dostarczone w ramach podejścia wtyczki.

 Aby zaimplementować pakietu VSPackage kontroli źródła, należy:

1. Utwórz i zarejestruj własne pakietu VSPackage kontroli źródła zgodnie z opisem w temacie [rejestracja i wybór](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

2. Zastąp domyślny interfejs użytkownika kontroli źródła własnym interfejsem użytkownika. Zobacz [niestandardowy interfejs użytkownika](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Określ glify, które mają być używane, i obsłuż **Eksplorator rozwiązań** zdarzenia symboli. Zobacz [kontrolka symbol](../../extensibility/internals/glyph-control-source-control-vspackage.md).

4. Obsługa zdarzeń edycji zapytań i zapisywania zapytań, jak pokazano w kwerendzie [Edycja zapytania Zapisz](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).

   Aby uzyskać więcej informacji, zobacz [Tworzenie pakietu VSPackage kontroli źródła](../../extensibility/internals/creating-a-source-control-vspackage.md).

## <a name="see-also"></a>Zobacz też
- [Omówienie](../../extensibility/internals/source-control-integration-overview.md)
- [Tworzenie wtyczki kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)
