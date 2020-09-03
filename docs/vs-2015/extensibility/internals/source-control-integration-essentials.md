---
title: Podstawowe informacje o integracji kontroli źródła | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b9189b647baa29d72975f84172696ecb54cd7f87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183430"
---
# <a name="source-control-integration-essentials"></a>Podstawowe informacje o integracji kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsługuje dwa typy integracji kontroli źródła: Wtyczka kontroli źródła, która zapewnia podstawowe funkcje i jest tworzona przy użyciu interfejsu API kontroli źródła (dawniej znanego jako interfejs API MSSCCI), oraz rozwiązania integracji kontroli źródła opartego na pakietu VSPackage, które zapewnia bardziej niezawodne funkcje.  
  
## <a name="source-control-plug-in"></a>Wtyczka kontroli źródła  
 Wtyczka do kontroli źródła jest zapisywana jako biblioteka DLL, która implementuje interfejs API wtyczki kontroli źródła. Funkcje integracji i kontroli źródła są udostępniane za pomocą interfejsu API. Takie podejście jest łatwiejsze do zaimplementowania niż pakietu VSPackage kontroli źródła i używa [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfejsu użytkownika (UI) w przypadku większości operacji kontroli źródła.  
  
 Aby zaimplementować wtyczkę kontroli źródła przy użyciu interfejsu API wtyczki kontroli źródła, wykonaj następujące kroki:  
  
1. Utwórz bibliotekę DLL, która implementuje funkcje określone w [wtyczkach kontroli źródła](../../extensibility/source-control-plug-ins.md).  
  
2. Zarejestruj bibliotekę DLL, wprowadzając odpowiednie wpisy rejestru zgodnie z opisem w temacie [How to: Install a Source Control plug-in](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3. Utwórz interfejs użytkownika pomocnika i Wyświetl go po wyświetleniu monitu przez pakiet adaptera kontroli źródła ( [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] składnik obsługujący funkcje kontroli źródła za pomocą wtyczek kontroli źródła).  
  
   Aby uzyskać więcej informacji, zobacz [tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>Pakietu VSPackage kontroli źródła  
 Implementacja pakietu VSPackage kontroli źródła pozwala opracowywać dostosowaną zamiennik dla [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfejsu użytkownika kontroli źródła. Takie podejście zapewnia pełną kontrolę nad integracją kontroli źródła, ale wymaga podania elementów interfejsu użytkownika i zaimplementowania interfejsów kontroli źródła, które w przeciwnym razie byłyby dostarczone w ramach podejścia wtyczki.  
  
 Aby zaimplementować pakietu VSPackage kontroli źródła, należy:  
  
1. Utwórz i zarejestruj własne pakietu VSPackage kontroli źródła zgodnie z opisem w temacie [rejestracja i wybór](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2. Zastąp domyślny interfejs użytkownika kontroli źródła własnym interfejsem użytkownika. Zobacz [niestandardowy interfejs użytkownika](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3. Określ glify, które mają być używane, i obsłuż **Eksplorator rozwiązań** zdarzenia symboli. Zobacz [kontrolka symbol](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4. Obsługa zdarzeń edycji zapytań i zapisywania zapytań, jak pokazano w kwerendzie [Edycja zapytania Zapisz](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
   Aby uzyskać więcej informacji, zobacz [Tworzenie pakietu VSPackage kontroli źródła](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Podsumowanie](../../extensibility/internals/source-control-integration-overview.md)   
 [Tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)
