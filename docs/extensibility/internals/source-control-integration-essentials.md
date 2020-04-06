---
title: Podstawowe informacje o integracji kontroli źródła | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e56658d644720f1563d71d3d08bf35268119112f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705236"
---
# <a name="source-control-integration-essentials"></a>Podstawowe informacje o integracji kontroli kodu źródłowego
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]obsługuje dwa typy integracji kontroli źródła: wtyczka kontroli źródła, która zapewnia podstawowe funkcje i jest zbudowana przy użyciu interfejsu API wtyczki kontroli źródła (wcześniej znanego jako interfejs API MSSCCI) oraz rozwiązania integracji kontroli źródła opartego na programie VSPackage, które zapewnia bardziej niezawodne funkcje.

## <a name="source-control-plug-in"></a>Wtyczka kontroli źródła
 Wtyczka kontroli źródła jest zapisywana jako biblioteka DLL, która implementuje interfejs API wtyczki kontroli źródła. Funkcja integracji rejestracji i kontroli źródła jest dostępna za pośrednictwem interfejsu API. Takie podejście jest łatwiejsze do zaimplementowania niż formantu źródła VSPackage i używa interfejsu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] użytkownika (UI) dla większości operacji kontroli źródła.

 Aby zaimplementować wtyczkę kontroli źródła przy użyciu interfejsu API dodatku Plug-in wtyczki kontroli źródła, wykonaj następujące kroki:

1. Utwórz bibliotekę DLL, która implementuje funkcje określone w [wtyczkach kontroli źródła](../../extensibility/source-control-plug-ins.md).

2. Zarejestruj bibliotekę DLL, dokonując odpowiednich wpisów rejestru, zgodnie z opisem w [jak: Zainstaluj wtyczkę kontroli źródła](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).

3. Utwórz pomocniczy interfejs użytkownika i wyświetl go po wyświetleniu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitu przez pakiet karty kontroli źródła (składnik, który obsługuje funkcje sterowania źródłem za pośrednictwem wtyczek kontroli źródła).

   Aby uzyskać więcej informacji, zobacz [Tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md).

## <a name="source-control-vspackage"></a>Kontrola źródła VSPackage
 Implementacja vspackage kontroli źródła umożliwia opracowanie niestandardowego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zastąpienia interfejsu użytkownika kontroli źródła. Takie podejście zapewnia pełną kontrolę nad integracji kontroli źródła, ale wymaga, aby zapewnić elementy interfejsu użytkownika i zaimplementować interfejsy kontroli źródła, które w przeciwnym razie zostałyby dostarczone w ramach podejścia dodatku.

 Aby zaimplementować formant źródła VSPackage, należy:

1. Utwórz i zarejestruj własną kontrolę źródła VSPackage, zgodnie z opisem w [rejestracji i zaznaczeniu](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

2. Zastąp domyślny interfejs użytkownika formantu źródła niestandardowym interfejsem użytkownika. Zobacz [Niestandardowy interfejs użytkownika](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Określ glify, które mają być używane, i obsłużyć zdarzenia glifów **Eksploratora rozwiązań.** Zobacz [Kontrola glifów](../../extensibility/internals/glyph-control-source-control-vspackage.md).

4. Objadź zdarzenia edycji kwerendy i zapisywania kwerend, jak pokazano w [programie Zapis kwerendy.](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

   Aby uzyskać więcej informacji, zobacz [Tworzenie formantu źródła VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md).

## <a name="see-also"></a>Zobacz też
- [Omówienie](../../extensibility/internals/source-control-integration-overview.md)
- [Tworzenie wtyczki kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)
