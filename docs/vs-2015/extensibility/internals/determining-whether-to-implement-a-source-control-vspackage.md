---
title: Określanie, czy wdrożyć pakiet VSPackage kontroli kodu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cff53700dcd6a80f841108d5a2b486dcb0ba7a11
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60090845"
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Określanie, czy wdrożyć pakiet VSPackage kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W tej sekcji rosnącego wyboru wtyczek kontroli kodu źródłowego, kontrolę źródła pakietów VSPackage rozszerzania rozwiązania i zapewnia ogólnych wytycznych o wybieraniu ścieżki odpowiednie integracji kontroli źródła.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Rozwiązania kontroli źródła małych z ograniczonymi zasobami  
 Jeśli masz ograniczone zasoby i nie można obciążać obciążenie zapisywania pakietu kontroli źródła, można utworzyć wtyczki oparte na interfejsie API wtyczki kontroli źródła. Umożliwia to współpracują z pakietów kontroli kodu źródłowego i można przełączać się między wtyczek kontroli kodu źródłowego i pakietów na żądanie. Aby uzyskać więcej informacji, zobacz [Rejestracja i wybór](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Rozwiązania kontroli źródła dużych z zestawem funkcji Zaawansowane  
 Jeśli chcesz zaimplementować rozwiązanie do kontroli źródła, które oferuje model kontroli źródła sformatowanego odpowiednio nie są przechwytywane za pomocą interfejsu API wtyczki kontroli źródła, można rozważyć pakietu kontroli źródła jako ścieżka integracji. Dotyczy to zwłaszcza, jeśli wolisz spowodowałoby zastąpienie pakietu karty kontroli źródła, (która komunikuje się z wtyczek kontroli kodu źródłowego i udostępnia kontrolkę interfejsu użytkownika podstawowego źródła) za pomocą własnych, dzięki czemu można obsługiwać zdarzenia kontroli źródła w sposób niestandardowy. Jeśli masz już źródłem zadowalający kontroli interfejsu użytkownika i chcesz zachować środowiska w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], opcji pakietu kontroli źródła umożliwia spełniają właśnie tę funkcję. Pakiet kontroli źródła nie jest ogólna i jest przeznaczona wyłącznie do użytku z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 Jeśli chcesz zaimplementować rozwiązanie do kontroli źródła, które zapewnia elastyczność i bardziej rozbudowane kontroli za pośrednictwem interfejsu użytkownika i logikę kontroli źródła, możesz trasy integracji pakietu kontroli źródła. Można:  
  
1. Rejestrowanie własnych kontroli źródła pakietu VSPackage (zobacz [Rejestracja i wybór](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2. Zamień kontroli źródła domyślny interfejs użytkownika niestandardowego interfejsu użytkownika (zobacz [niestandardowy interfejs użytkownika](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3. Określ symbole, można użyć do obsługi zdarzeń symbol w Eksploratorze rozwiązań (zobacz [kontrola symboli](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4. Obsługa zdarzeń zapytania, edytowanie i zapisywanie zapytań (zobacz [zapytania Edytuj zapytanie Zapisz](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie wtyczki kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-plug-in.md)
