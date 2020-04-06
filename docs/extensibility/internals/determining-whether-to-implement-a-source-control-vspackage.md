---
title: Określanie, czy zaimplementować vspackage kontroli źródła | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8707f3c1ced1cc2df9d3ae77280fc8779874a837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708718"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>Określanie, czy formant źródła VSPackage ma zostać zaimplementowane
W tej sekcji opracowywane są opcje wtyczek kontroli źródła i kontroli źródła VSPackages do rozszerzania rozwiązań kontroli źródła i zawiera ogólne wskazówki dotyczące wyboru odpowiedniej ścieżki integracji.

## <a name="small-source-control-solution-with-limited-resources"></a>Małe rozwiązanie do kontroli źródeł z ograniczonymi zasobami
 Jeśli masz ograniczone zasoby i nie można obciążyć obciążeniem związanym z pisaniem pakietu kontroli źródła, można utworzyć wtyczki oparte na interfejsie API dodatku Forkwa. Aby uzyskać więcej informacji, zobacz [Rejestracja i wybór](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Duże rozwiązanie do sterowania źródłem z bogatym zestawem funkcji
 Jeśli chcesz zaimplementować rozwiązanie kontroli źródła, który zapewnia model kontroli źródła zaawansowanego, który nie jest odpowiednio przechwycony przy użyciu interfejsu API wtyczki kontroli źródła, można rozważyć pakiet kontroli źródła jako ścieżkę integracji. Dotyczy to zwłaszcza, jeśli wolisz zastąpić pakiet karty kontroli źródła (który komunikuje się z wtyczkami kontroli źródła i zapewnia podstawowy interfejs użytkownika kontroli źródła) z własnym, dzięki czemu można obsługiwać zdarzenia kontroli źródła w sposób niestandardowy. Jeśli masz już zadowalający interfejs użytkownika kontroli źródła i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]chcesz zachować to doświadczenie w , opcja pakietu kontroli źródła pozwala to zrobić. Pakiet kontroli źródła nie jest ogólny i jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przeznaczony wyłącznie do użytku z IDE.

 Jeśli chcesz zaimplementować rozwiązanie kontroli źródła, które zapewnia elastyczność i bogatszą kontrolę nad logiką kontroli źródła i interfejsem użytkownika, możesz preferować trasę integracji pakietu kontroli źródła. Możesz:

1. Zarejestruj własną kontrolę źródła VSPackage (zobacz [Rejestracja i wybór](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).

2. Zastąp domyślny interfejs użytkownika formantu źródła niestandardowym interfejsem użytkownika (zobacz [Niestandardowy interfejs użytkownika).](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

3. Określ glify, które mają być używane, i obsłużyć zdarzenia glifów Eksploratora rozwiązań (patrz [kontrola glifów).](../../extensibility/internals/glyph-control-source-control-vspackage.md)

4. Obsługa zdarzeń edycji kwerendy i zapisywania kwerend (zobacz [Zapisywanie kwerendy .](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

## <a name="see-also"></a>Zobacz też
- [Tworzenie wtyczki formantu źródła](../../extensibility/internals/creating-a-source-control-plug-in.md)
