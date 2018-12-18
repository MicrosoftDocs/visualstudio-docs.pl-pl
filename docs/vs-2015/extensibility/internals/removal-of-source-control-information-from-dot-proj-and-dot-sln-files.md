---
title: Usuwanie z, informacje o kontroli źródła. Proj i. Pliki SLN | Dokumentacja firmy Microsoft
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
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 850f2278480b27eb302fe9cc87c608c0cd522e38
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761546"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Usuwanie informacji o kontroli kodu źródłowego z plików Proj i Sln
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W wersji 1.2 API wtyczki kontroli źródła SCC informacje są przechowywane w MSSCCPRJ. Plik SCC. Zaletą MSSCCPRJ. Plik SCC jest o tym, czy informacje SCC jest nie źródła - kontrolowane, tak jak w przypadku plików Proj i sln.  
  
## <a name="version-12-changes"></a>Zmiany w wersji 1.2  
 W źródła wtyczek kontroli, które są oparte na API wtyczki kontroli źródła w wersji 1.1 informacje o kontroli źródła znajduje się w projekcie (plików Proj) i pliki rozwiązania (.sln). Lokalizacja bazy danych informacji dotyczących kontroli źródła jest określona przez AuxPath, a określonej lokalizacji w bazie danych jest określona przez ProjName. To zachowanie może powodować problemy po gałęzi, rozwidlenia lub operacji kopiowania, ponieważ ProjName zwykle są nieprawidłowe po każdym z tych operacji.  
  
 W interfejsie API wtyczki kontroli źródła w wersji 1.1, IDE używane ~ SAK plików, aby wykryć, czy dodatek typu plug-in obsługiwana MSSCCPRJ. Metoda SCC przechowywania informacje kontroli źródła. API wtyczki kontroli źródła w wersji 1.2 zapewnia nowe możliwości wykrywania obsługę MSSCCPRJ. Plik SCC bez użycia ~ SAK pliku. Aby uzyskać więcej informacji, zobacz [eliminacja ~ SAK pliki](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

