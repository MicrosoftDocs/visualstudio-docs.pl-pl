---
title: 'Instrukcje: Programowe wyszukiwanie w określonym folderze'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: d9a08451b186cdc3ca1526441e906cf3c9e5d4c9
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866847"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Instrukcje: Programowe wyszukiwanie w określonym folderze
  W tym przykładzie kodu użyto `Find` i `FindNext` metody, aby wyszukać tekst w polu tematu wiadomości e-mail, które znajdują się w **skrzynki odbiorczej**. Ta metoda używa filtru ciągów pod kątem litera T jako początkowa litera `Subject` tekstu.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z folderami](../vsto/working-with-folders.md)   
 [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)   
 [Instrukcje: Programowe pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
