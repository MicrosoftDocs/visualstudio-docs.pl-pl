---
title: Podstawowe informacje o integracji kontroli źródła | Dokumentacja firmy Microsoft
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
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9893d5525bf66b167dea170c0c5fae8285aa40af
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780974"
---
# <a name="source-control-integration-essentials"></a>Podstawowe informacje o integracji kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsługuje dwa typy Integracja kontroli źródła: wtyczka do kontroli źródła zapewnia podstawowe funkcje, który został skompilowany przy użyciu interfejsu API wtyczki kontroli źródła (znanego wcześniej jako interfejs API MSSCCI) i rozwiązania integracji kontroli źródła opartych na VSPackage, zapewnia bardziej niezawodne funkcje.  
  
## <a name="source-control-plug-in"></a>Wtyczka do kontroli źródła  
 Wtyczki kontroli źródła jest zapisywany jako bibliotekę DLL, która implementuje interfejs API wtyczki kontroli źródła. Funkcje integracji kontroli rejestracji i źródła znajduje się za pośrednictwem interfejsu API. Ta metoda jest prostsza do zaimplementowania niż pakietu VSPackage kontroli źródła, przy czym [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfejs użytkownika (UI) dla większości operacji kontroli źródła.  
  
 Aby zaimplementować wtyczka do kontroli źródła przy użyciu interfejsu API wtyczki kontroli źródła, wykonaj następujące kroki:  
  
1. Tworzenie biblioteki DLL, która implementuje funkcje wymienione w [wtyczki kontroli źródła](../../extensibility/source-control-plug-ins.md).  
  
2. Zarejestruj plik DLL, wprowadzając wpisy rejestru odpowiednich, zgodnie z opisem w [porady: Instalowanie wtyczki kontroli źródła](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3. Utwórz obiekt pomocnika interfejsu użytkownika i wyświetl ją po wyświetleniu monitu przez pakiet karty kontroli źródła ( [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] składnik, który obsługuje funkcji kontroli źródła przy użyciu wtyczki kontroli źródła).  
  
   Aby uzyskać więcej informacji, zobacz [tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>Pakiet VSPackage kontroli  
 Kontroli źródła pakietu VSPackage implementacji umożliwia tworzenie dostosowanych zastępuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] źródłowej kontrolki interfejsu użytkownika. To podejście zapewnia pełną kontrolę nad Integracja kontroli źródła, ale wymaga ona Podaj elementy interfejsu użytkownika, a także implementować interfejsy kontroli źródła, które będą dostarczane w ramach wtyczki podejście.  
  
 Aby zaimplementować pakietu VSPackage kontroli źródła, musisz mieć:  
  
1. Tworzenie i rejestrowanie własnych kontroli źródła pakietu VSPackage, zgodnie z opisem w [Rejestracja i wybór](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2. Zastąp kontroli źródła domyślny interfejs użytkownika niestandardowego interfejsu użytkownika. Zobacz [niestandardowego interfejsu użytkownika](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3. Określ symbole, można użyć w celu obsługi **Eksploratora rozwiązań** symbol zdarzenia. Zobacz [kontrola symboli](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4. Obsługa zdarzeń zapytania, edytować i zapisywać zapytania, jak pokazano na [zapytania Edytuj zapytanie Zapisz](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
   Aby uzyskać więcej informacji, zobacz [tworzenia VSPackage kontroli kodu](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../../extensibility/internals/source-control-integration-overview.md)   
 [Tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)

