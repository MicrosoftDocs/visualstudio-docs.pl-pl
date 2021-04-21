---
title: Programowe znajdowanie adresu e-mail w kontaktach
description: Dowiedz się, jak używać Visual Studio, aby programowo znaleźć adres e-mail w kontaktach programu Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cd977840cd75081d87011540ca00675fb84cee36
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828946"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>How to: Programowe wyszukiwanie adresu e-mail w kontaktach
  Ten przykład wyszukuje w folderze kontaktów kontakty, które mają nazwę **example.com** w ich adresach e-mail.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 Ten przykład wymaga:

- Kontakty, które mają nazwę **example.com** w adresach e-mail (na przykład ), i które `somebody@example.com` mają imiona i nazwiska.

## <a name="see-also"></a>Zobacz też
- [Praca z elementami kontaktów](../vsto/working-with-contact-items.md)
- [Jak programowo wysyłać wiadomości e-mail](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Szybki start: Programowy dostęp do kontaktów programu Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Jak programowo dodać wpis do kontaktów programu Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
