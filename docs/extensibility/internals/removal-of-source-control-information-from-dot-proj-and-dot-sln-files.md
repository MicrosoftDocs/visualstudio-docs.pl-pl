---
title: Usuń informacje o kontroli źródła z plików Proj i SLN
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
ms.openlocfilehash: 081766a8169ccc54888a076012b8281c485a20e5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318821"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Usuwanie informacji o kontroli kodu źródłowego z plików Proj i Sln
W wersji 1.2 API wtyczki kontroli źródła SCC informacje są przechowywane w MSSCCPRJ. Plik SCC. Zaletą MSSCCPRJ. Plik SCC jest o tym, czy informacje SCC jest nie źródła - kontrolowane, tak jak w przypadku plików Proj i sln.

## <a name="version-12-changes"></a>Zmiany w wersji 1.2
 W źródła wtyczek kontroli, które są oparte na API wtyczki kontroli źródła w wersji 1.1 informacje o kontroli źródła znajduje się w projekcie (plików Proj) i pliki rozwiązania (.sln). Lokalizacja bazy danych informacji dotyczących kontroli źródła jest określona przez AuxPath, a określonej lokalizacji w bazie danych jest określona przez ProjName. To zachowanie może powodować problemy po gałęzi, rozwidlenia lub operacji kopiowania, ponieważ ProjName zwykle są nieprawidłowe po każdym z tych operacji.

 W interfejsie API wtyczki kontroli źródła w wersji 1.1, IDE używane ~ SAK plików, aby wykryć, czy dodatek typu plug-in obsługiwana MSSCCPRJ. Metoda SCC przechowywania informacje kontroli źródła. API wtyczki kontroli źródła w wersji 1.2 zapewnia nowe możliwości wykrywania obsługę MSSCCPRJ. Plik SCC bez użycia ~ SAK pliku. Aby uzyskać więcej informacji, zobacz [eliminacja ~ SAK pliki](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Zobacz też
- [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)