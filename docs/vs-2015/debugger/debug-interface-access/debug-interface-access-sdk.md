---
title: Zestaw SDK dostępu do interfejsu debugowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ddaea95bc879364de99c0ec01213cda30fa4e7d7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197622"
---
# <a name="debug-interface-access-sdk"></a>Zestaw SDK dostępu do interfejsu debugowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Microsoft debugowanie interfejsu dostępu Software Development Kit (DIA SDK) zapewnia dostęp do debugowania informacje przechowywane w plikach bazy danych (PDB) program wygenerowanych przez postcompiler narzędzi firmy Microsoft. Ponieważ format pliku PDB wygenerowany za pomocą narzędzi postcompiler ulega stałej poprawki, udostępnianie format jest niepraktyczne. Za pomocą interfejsu API DIA, można tworzyć aplikacje, które wyszukiwać i przeglądać informacje debugowania przechowywane w pliku .pdb. Takie aplikacje można na przykład zgłaszania informacji dotyczących zdarzenia sprzed stosu i analizowanie danych dotyczących wydajności.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Zawiera omówienie DIA SDK funkcji oraz określa, gdzie DIA SDK jest zainstalowany, a także wymagany nagłówek i pliki biblioteki.  
  
 [Używanie zapytań dotyczących pliku .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Instrukcje dotyczące sposobu używania interfejsu API DIA pliku .pdb kwerendy.  
  
 [Symbole i tagi symboli](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 W tym artykule omówiono sposób symbole i tagi symboli są używane w interfejsie API DIA.  
  
 [Dokumentacja](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Zawiera interfejsy, metody, wyliczenia i struktury DIA interfejsu API.  
  
 [Dia2dump — przykład](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Ilustruje sposób wyszukiwać i przeglądać informacje o debugowaniu za pomocą interfejsu API DIA.  
  
 [Plik źródłowy Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Używane przez kod źródłowy [dia2dump — przykład](../../debugger/debug-interface-access/dia2dump-sample.md) aby zademonstrować DIA interfejsu API.
