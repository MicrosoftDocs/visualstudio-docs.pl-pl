---
title: Usuwanie informacji o kontroli źródła z plików .proj i .sln
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba3085a7806bfb0556613d1fca1b94953dcdb0b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705588"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Usuwanie informacji o kontroli kodu źródłowego z plików Proj i Sln
W wersji 1.2 interfejsu API wtyczki kontroli źródła informacje SCC są przechowywane w mssccprj. SCC. Zaletą MSSCCPRJ. SCC plik jest to, że informacje SCC nie jest źródło kontrolowane, jak to jest w .proj i .sln plików.

## <a name="version-12-changes"></a>Zmiany w wersji 1.2
 W wtyczkach kontroli źródła, które są oparte na interfejsie API wtyczki kontroli źródła w wersji 1.1, informacje o kontroli źródła są przechowywane w plikach projektu (.proj) i rozwiązania (.sln). Lokalizacja bazy danych informacji kontroli źródła jest określona przez AuxPath, a określona lokalizacja w bazie danych jest określona przez ProjName. To zachowanie może powodować problemy po operacji gałęzi, rozwidla lub kopiowania, ponieważ ProjName zazwyczaj jest nieprawidłowy po dowolnej z tych operacji.

 W interfejsie API wtyczki kontroli źródła w wersji 1.1 IDE używane pliki ~SAK do wykrywania, czy dodatek obsługuje MSSCCPRJ. Metoda SCC przechowywania informacji o kontroli źródła. Interfejs API wtyczki kontroli źródła w wersji 1.2 zapewnia nową możliwość wykrywania obsługi mssccprj. SCC bez użycia pliku ~SAK. Aby uzyskać więcej informacji, zobacz [Eliminacja plików ~SAK](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Zobacz też
- [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
