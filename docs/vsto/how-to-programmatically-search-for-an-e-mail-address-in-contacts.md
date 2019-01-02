---
title: 'Instrukcje: Programowe wyszukiwanie adresu e-mail w kontaktach'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 767c75bff42bc19b70d4b6dcd35da16c4bb4c099
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893357"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>Instrukcje: Programowe wyszukiwanie adresu e-mail w kontaktach
  W tym przykładzie wyszukuje skontaktuj się z folderu kontaktów, które mają taką nazwę domeny **example.com** w ich adresy e-mail.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Ten przykład wymaga:  
  
-   Kontakty, które mają taką nazwę domeny **example.com** w ich adresy e-mail (na przykład `somebody@example.com`), których imiona i nazwiska.  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z elementami kontaktów](../vsto/working-with-contact-items.md)   
 [Instrukcje: Programowo Wyślij wiadomość e-mail](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [Instrukcje: Programowy dostęp do kontaktów programu Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Instrukcje: Programowe Dodawanie wpisu do kontaktów programu Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
