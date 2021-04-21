---
title: Jak programowo wysyłać wiadomości e-mail
description: Użyj Visual Studio, aby programowo wysłać wiadomość e-mail z programu Microsoft Outlook. W tym przykładzie wiadomość e-mail jest wysyłana do kontaktów, które mają nazwę example.com.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fa6a45a199d4edce924f0e36a971026726d96eca
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824799"
---
# <a name="how-to-programmatically-send-email"></a>Jak programowo wysyłać wiadomości e-mail
  W tym przykładzie wysyła wiadomość e-mail do kontaktów, które mają nazwę **example.com** w ich adresach e-mail.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="example"></a>Przykład
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 Ten przykład wymaga:

- Kontakty, które mają nazwę **domeny example.com** adresach e-mail.

## <a name="robust-programming"></a>Niezawodne programowanie
 Nie usuwaj kodu filtru, który wyszukuje nazwę domeny w **example.com**. Rozwiązanie będzie wysyłać wiadomości e-mail do wszystkich twoich kontaktów, jeśli usuniesz filtr.

## <a name="see-also"></a>Zobacz też
- [Praca z elementami poczty](../vsto/working-with-mail-items.md)
- [Tworzyć programowo element wiadomości e-mail](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Szybki start: Programowe uzyskiwanie dostępu do kontaktów programu Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Dzieje się tak: Programowe wykonywanie akcji po otrzymaniu wiadomości e-mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
