---
title: Usuń informacje o kontroli źródła z plików. proj i. sln
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68e50932a83e3db6d405119d3721d021144cbaeb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724276"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Usuwanie informacji o kontroli kodu źródłowego z plików Proj i Sln
W wersji 1,2 interfejsu API dodatku plug-in kontroli źródła informacje o SCC są przechowywane w MSSCCPRJ. Plik SCC. Zaletą MSSCCPRJ. Plik SCC to informacja, że informacje SCC nie są kontrolowane przez źródło, takie jak w plikach. proj i. sln.

## <a name="version-12-changes"></a>Zmiany w wersji 1,2
 W wtyczkach kontroli źródła, które są oparte na interfejsie API wtyczki kontroli źródła w wersji 1,1, informacje o kontroli źródła są przechowywane w plikach projektu (. proj) i rozwiązania (. sln). Lokalizacja bazy danych informacji o kontroli źródła jest określana przez AuxPath, a określona lokalizacja w bazie danych jest określana przez Projname. Takie zachowanie może spowodować problemy po operacji rozgałęzienia, rozwidlenia lub kopiowania, ponieważ Projname zwykle jest nieważny po którejkolwiek z tych operacji.

 W interfejsie API dodatku plug-in kontroli źródła w wersji 1,1 środowisko IDE używane ~ SAK pliki do wykrycia, czy wtyczka obsługuje MSSCCPRJ. Metoda SCC przechowująca informacje o kontroli źródła. Interfejs API wtyczki kontroli źródła w wersji 1,2 oferuje nową funkcję wykrywania obsługi MSSCCPRJ. Plik SCC bez użycia pliku ~ SAK. Aby uzyskać więcej informacji, zobacz [eliminacja plików ~ SAK](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Zobacz także
- [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)