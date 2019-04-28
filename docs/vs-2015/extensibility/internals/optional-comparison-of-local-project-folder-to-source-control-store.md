---
title: Opcjonalne Porównanie lokalnego folderu projektu do Store kontroli źródła | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: be26b4195e0db7b3b78fcc2223ff2a6f8bde47d3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438937"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Opcjonalne porównanie lokalnego folderu projektu do magazynu kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W źródle kontrolować 1.2 interfejsu API wtyczki porównania między lokalnym folderze projektu i kontrola źródła odbywa się za pomocą funkcji [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) i [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 W ramach **Eksploratora rozwiązań**, jeśli wybrano folderu zamiast pojedynczego pliku, **Porównaj wersje** menu skrótów wywołuje nowej [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) i [ SccDirDiff](../../extensibility/sccdirdiff-function.md) w wtyczka do kontroli źródła.  
  
## <a name="new-capability-flags"></a>Nowe flagi możliwości  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Nowe funkcje  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 `SccDirQueryInfo` Funkcja jest wywoływana przed `SccDirDiff` do ustalenia, czy katalog roboczy jest pod kontrolą źródła. `SccDirDiff` Funkcja wyświetla różnice między bieżącym katalogu lokalnego i odpowiedni folder kontroli źródła. To polecenie pyta, czy wtyczka do kontroli źródła Aby wyświetlić listę zmian w katalogu. Wtyczka do kontroli źródła udostępnia własny interfejs użytkownika do wyświetlania różnic.  
  
> [!NOTE]
> Ta funkcja używa tego samego flag poleceń jako [SccDiff](../../extensibility/sccdiff-function.md). Jako dostawca wtyczki kontroli źródła istnieje możliwość nie obsługuje operacji "szybkie diff" w przypadku katalogów.  
  
## <a name="see-also"></a>Zobacz też  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
