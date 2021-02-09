---
title: 'Instrukcje: programowe wyszukiwanie określonego kontaktu'
description: Dowiedz się, jak używać programu Visual Studio do programistycznego wyszukiwania określonego kontaktu w programie Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: afe17292db70f2d2fdd16e7c7b388343fbf9db9c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841953"
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>Instrukcje: programowe wyszukiwanie określonego kontaktu
  Ten przykład przeszukuje folder Kontakty programu Outlook pod kątem określonego kontaktu według imienia i nazwiska. W przykładzie przyjęto założenie, że kontakt o nazwie **Jan Evans** istnieje w folderze kontaktów.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb#1)]

## <a name="see-also"></a>Zobacz także
- [Pracuj z elementami kontaktów](../vsto/working-with-contact-items.md)
- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
