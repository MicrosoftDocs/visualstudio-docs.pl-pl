---
title: Zestaw SDK dostępu do interfejsu debugowania | Dokumentacja firmy Microsoft
ms.date: 07/24/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 915f594a984af41da167e0fd3d58beb2f6ddd978
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608087"
---
# <a name="debug-interface-access-sdk"></a>Zestaw SDK dostępu do interfejsu debugowania

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
