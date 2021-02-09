---
title: Wyświetlanie dokumentów skryptów | Microsoft Docs
description: Dowiedz się, jak wyświetlać dokumenty skryptów po stronie serwera JavaScript w programie Visual Studio przy użyciu Eksplorator rozwiązań.
ms.custom: SEO-VS-2020
ms.date: 11/05/2019
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cfaa4e2558d8d1f102b0e442e9c509313f860e4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853101"
---
# <a name="how-to-view-script-documents-javascript"></a>Instrukcje: wyświetlanie dokumentów skryptów (JavaScript)

Pliki skryptów po stronie serwera są widoczne w Eksplorator rozwiązań. Pliki skryptów po stronie klienta są widoczne tylko wtedy, gdy jesteś w trybie debugowania lub w trybie przerwania. Pliki skryptów po stronie klienta są wyświetlane w węźle **dokumenty skryptu** .

W przypadku niektórych typów aplikacji, które dynamicznie generują strony, łatwiej jest wejść w tryb przerwania i debugowanie, gdy ustawisz punkt przerwania na podstawie dokumentu skryptu, który jest ładowany w przeglądarce. Podobnie można dodać `debugger` instrukcję z załadowanego dokumentu skryptu w celu przejścia do trybu przerwania. W tym artykule przedstawiono sposób wyświetlania tych dokumentów.

> [!NOTE]
> Poprzednie względem [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] , pliki skryptów po stronie klienta generowane przez skrypt po stronie serwera pojawiły się w oknie Eksplorator skryptów.

### <a name="to-view-a-server-side-script-document"></a>Aby wyświetlić dokument skryptu po stronie serwera

1. W **Eksplorator rozwiązań** Otwórz **\<Website Pathname>** węzeł.

2. Kliknij dwukrotnie plik skryptu, który chcesz wyświetlić.

     Plik skryptu po stronie serwera zostanie otwarty w oknie źródła.

### <a name="to-view-a-client-side-script-document"></a>Aby wyświetlić dokument skryptu po stronie klienta

1. W **Eksplorator rozwiązań** Otwórz węzeł **dokumenty skryptu** .

2. Kliknij dwukrotnie plik skryptu, który chcesz wyświetlić.

     Plik skryptu po stronie klienta zostanie otwarty w oknie źródła.

## <a name="see-also"></a>Zobacz też
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)