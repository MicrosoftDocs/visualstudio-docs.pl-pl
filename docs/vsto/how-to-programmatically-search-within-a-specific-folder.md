---
title: 'Instrukcje: programowe wyszukiwanie w określonym folderze'
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
ms.openlocfilehash: 8f5e0f098edcffce07eb2c3f243b994d1a53cdf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547020"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Instrukcje: programowe wyszukiwanie w określonym folderze
  Ten przykład kodu używa `Find` metod i, `FindNext` Aby wyszukać tekst w polu podmiotu wiadomości e-mail znajdujących się w **skrzynce odbiorczej**. Ta metoda używa filtru ciągów, aby wyszukać literę T jako początkową literę `Subject` tekstu.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Zobacz też
- [Pracuj z folderami](../vsto/working-with-folders.md)
- [Model obiektów programu Outlook — Omówienie](../vsto/outlook-object-model-overview.md)
- [Instrukcje: programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
