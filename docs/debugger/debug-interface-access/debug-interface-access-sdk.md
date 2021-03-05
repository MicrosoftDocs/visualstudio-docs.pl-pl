---
description: Pakiet Microsoft Debug Interface Access Software Development Kit (DIA SDK) zapewnia dostęp do informacji debugowania przechowywanych w plikach bazy danych programu (. pdb) wygenerowanych przez narzędzia Microsoft postcompiler Tools.
title: Zestaw SDK dostępu do interfejsu debugowania | Microsoft Docs
ms.date: 07/24/2018
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fbb7c9025094249715f1d69a8d58d8725d294107
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149305"
---
# <a name="debug-interface-access-sdk"></a>Zestaw SDK dostępu do interfejsu debugowania

Pakiet Microsoft Debug Interface Access Software Development Kit (DIA SDK) zapewnia dostęp do informacji debugowania przechowywanych w plikach bazy danych programu (. pdb) wygenerowanych przez narzędzia Microsoft postcompiler Tools. Ponieważ format pliku. pdb wygenerowanego przez narzędzia postcompiler nie przeprowadzi stałej korekty, ujawnienie formatowania jest niepraktyczne. Korzystając z interfejsu API DIA, można opracowywać aplikacje, które przeszukują i przeglądają informacje debugowania przechowywane w pliku. pdb. Mogą to być takie aplikacje, na przykład informacje o śledzeniu stosu raportów i analizowanie danych wydajności.

## <a name="in-this-section"></a>W tej sekcji

[Wprowadzenie](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)

Zawiera przegląd funkcji DIA SDK i określa, gdzie jest zainstalowana DIA SDK, oraz wymaganych plików nagłówkowych i bibliotek.

[Używanie zapytań dotyczących pliku .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

Zawiera instrukcje dotyczące korzystania z interfejsu API DIA w celu wykonywania zapytań dotyczących pliku. pdb.

[Symbole i tagi symboli](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)

Omawia, w jaki sposób symbole i Tagi symboli są używane w interfejsie API DIA.

[Odwołanie](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)

Zawiera interfejsy, metody, wyliczenia i struktury interfejsu API DIA.

[Dia2dump — przykład](../../debugger/debug-interface-access/dia2dump-sample.md)

Ilustruje sposób używania interfejsu API DIA do wyszukiwania i przeglądania informacji debugowania.
