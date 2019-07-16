---
title: Co&#39;s Nowość w źródle kontrolować wtyczki API w wersji 1.3 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d5333a5b44e9c990843e66da357578e4a90d210
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200929"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Co&#39;s Nowość w źródle kontrolować wtyczki API w wersji 1.3
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

API wtyczki kontroli źródła w wersji 1.3 wprowadzono następujące nowe funkcje do zapewnienia bardziej zaawansowanych kontroli.  
  
## <a name="changes"></a>Zmiany  
 Jesteś nowym użytkownikiem API wtyczki kontroli źródła w wersji 1.3 są następujące funkcje:  
  
|Funkcja|Omówienie|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Zezwala na dodatkowe możliwości usługi bits, należy podać|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Umożliwia badanie plików, które mają nowszych wersji w bazie danych kontroli wersji niż na dysku lokalnym|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Umożliwia badanie stanu zmiany nazwy (zmienia nazwę, dodań i usunięć) dla określonych plików|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Umożliwia badanie plików i katalogów w bazie danych kontroli wersji|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Określona lista plików z bazy danych kontroli wersji są dodawane do bieżącego projektu|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Wykonuje silent "Pobierz" określonych plików (bez interfejsu użytkownika znajduje się)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Zezwala na dostęp do opcji specyficzne dla użytkownika|  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
