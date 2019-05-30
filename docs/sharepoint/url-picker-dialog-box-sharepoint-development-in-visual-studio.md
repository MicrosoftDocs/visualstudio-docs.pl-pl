---
title: Okno dialogowe selektora URL (Programowanie SharePoint)
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 991693c3379e008a2a907efd3127290c7e804c22
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261945"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Okno dialogowe selektora URL (Programowanie SharePoint w programie Visual Studio)
  W okno dialogowe selektora URL można wybrać pliki, takie jak pliki strony wzorcowej lub pliki obrazów, które znajdują się w projekcie lub na serwerze lokalnym, na którym uruchomiony jest SharePoint.

 To okno dialogowe pojawia się, gdy masz opcję, aby wybrać plik do ustawiania właściwości. To okno dialogowe można otworzyć, wybierając przycisk wielokropka (![elipsy projektanta Mobile ASP.NET](../sharepoint/media/mwellipsis.gif "elipsy projektanta Mobile ASP.NET")) obok różne właściwości w **właściwości** okna. Przycisk wielokropka są także przedstawione jako IntelliSense monitu podczas przypisywania wartości do określonych atrybutów w **źródła** Widok projektanta.

## <a name="uielement-list"></a>Lista elementów interfejsu użytkownika
 **Foldery projektu** Wyświetla listę folderów zdefiniowane w projekcie lub na serwerze lokalnym, na którym uruchomiony jest SharePoint. Wybierz przycisk rozszerzenia, aby wyświetlić jego podfolderach.

 Rozwiń **projektu** węzeł, aby wybrać pliki w projekcie. Aby w oknie dialogowym są wyświetlane jako możliwy, pliki w projekcie musi spełniać następujące kryteria:

- Plik musi być zawarty w zamapowany folder.

- Konieczne jest dodanie pliku do pakietu rozwiązań.

- Plik nie może znajdować się w innym projekcie.

  Aby odwoływać się do plików, które nie spełniają tych kryteriów, musisz ręcznie wprowadź ścieżkę pliku.

  Rozwiń **serwera** węzeł, aby wybrać pliki, które znajdują się na serwerze lokalnym, na którym uruchomiony jest SharePoint. Aby w oknie dialogowym są wyświetlane jako możliwy, te pliki muszą spełniać następujące kryteria:

- Plik musi znajdować się w jednym z następujących folderów mapowanych: **Obrazy**, **układy**, lub **ControlTemplates**.

- Plik nie może znajdować się w bazie danych zawartości programu SharePoint.

  Aby odwoływać się do plików, które nie spełniają tych kryteriów, musisz ręcznie wprowadź ścieżkę pliku.

  **Zawartość folderu** Wyświetla listę plików w wybranym folderze. Wybierz plik, a następnie wybierz **OK** przycisk, aby zamknąć okno dialogowe i Wyślij zaznaczenie do procesu, który ją wywołuje.

  **Pliki typu** pozwala na wybranie z listy plików, które są odpowiednie dla zadania są wykonywane.

## <a name="see-also"></a>Zobacz także
- [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Tworzenie składników web Part programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
