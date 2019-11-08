---
title: 'Instrukcje: wyświetlanie dokumentów skryptów | Microsoft Docs'
ms.date: 11/05/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e362e0504c4ed2584bbbbea687fe3c58fc79edb
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73714440"
---
# <a name="how-to-view-script-documents-javascript"></a>Instrukcje: wyświetlanie dokumentów skryptów (JavaScript)

Pliki skryptów po stronie serwera są widoczne w Eksplorator rozwiązań. Pliki skryptów po stronie klienta są widoczne tylko wtedy, gdy jesteś w trybie debugowania lub w trybie przerwania. Pliki skryptów po stronie klienta są wyświetlane w węźle **dokumenty skryptu** .

W przypadku niektórych typów aplikacji, które dynamicznie generują strony, łatwiej jest wejść w tryb przerwania i debugowanie, gdy ustawisz punkt przerwania na podstawie dokumentu skryptu, który jest ładowany w przeglądarce. Podobnie można dodać instrukcję `debugger` z załadowanego dokumentu skryptu w celu przejścia do trybu przerwania. W tym artykule przedstawiono sposób wyświetlania tych dokumentów.

> [!NOTE]
> Po powrocie do [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]pliki skryptów po stronie klienta generowane przez skrypt po stronie serwera pojawiły się w oknie Eksplorator skryptów.

### <a name="to-view-a-server-side-script-document"></a>Aby wyświetlić dokument skryptu po stronie serwera

1. W **Eksplorator rozwiązań**Otwórz węzeł **ścieżki \<Website >** .

2. Kliknij dwukrotnie plik skryptu, który chcesz wyświetlić.

     Plik skryptu po stronie serwera zostanie otwarty w oknie źródła.

### <a name="to-view-a-client-side-script-document"></a>Aby wyświetlić dokument skryptu po stronie klienta

1. W **Eksplorator rozwiązań**Otwórz węzeł **dokumenty skryptu** .

2. Kliknij dwukrotnie plik skryptu, który chcesz wyświetlić.

     Plik skryptu po stronie klienta zostanie otwarty w oknie źródła.

## <a name="see-also"></a>Zobacz także
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)