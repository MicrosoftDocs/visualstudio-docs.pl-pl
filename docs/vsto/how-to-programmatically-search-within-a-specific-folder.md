---
title: 'Instrukcje: programowe wyszukiwanie w określonym folderze'
description: Dowiedz się, jak za pomocą programu Visual Studio programowo przeszukiwać w określonym folderze programu Microsoft Outlook.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fa569a2c301cb495f109a612d817937159c257c6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524541"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Instrukcje: programowe wyszukiwanie w określonym folderze
  Ten przykład kodu używa `Find` metod i, `FindNext` Aby wyszukać tekst w polu podmiotu wiadomości e-mail znajdujących się w **skrzynce odbiorczej**. Ta metoda używa filtru ciągów, aby wyszukać literę T jako początkową literę `Subject` tekstu.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Zobacz także
- [Pracuj z folderami](../vsto/working-with-folders.md)
- [Model obiektów programu Outlook — Omówienie](../vsto/outlook-object-model-overview.md)
- [Instrukcje: programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
