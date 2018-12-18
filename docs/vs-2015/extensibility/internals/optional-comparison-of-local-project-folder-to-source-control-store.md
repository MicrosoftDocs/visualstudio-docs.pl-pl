---
title: Opcjonalne Porównanie lokalnego folderu projektu do Store kontroli źródła | Dokumentacja firmy Microsoft
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
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 359b5e0e2eb3b2a90e3860bdd2664641580971d2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784107"
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
>  Ta funkcja używa tego samego flag poleceń jako [SccDiff](../../extensibility/sccdiff-function.md). Jako dostawca wtyczki kontroli źródła istnieje możliwość nie obsługuje operacji "szybkie diff" w przypadku katalogów.  
  
## <a name="see-also"></a>Zobacz też  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

