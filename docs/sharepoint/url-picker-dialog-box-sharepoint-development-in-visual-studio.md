---
title: Okno dialogowe selektora adresów URL (Programowanie SharePoint)
description: Dowiedz się więcej na temat okna dialogowego selektora adresów URL, które umożliwia użytkownikowi wybranie plików znajdujących się w ich projekcie lub na serwerze lokalnym, na którym działa program SharePoint.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d04857f0e61e5d9f293d73902cd090f718c65cd0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892219"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Okno dialogowe selektora adresów URL (Programowanie SharePoint w Visual Studio)
  W oknie dialogowym Selektor adresów URL możesz wybrać pliki, takie jak pliki strony głównej lub pliki obrazów, które znajdują się w projekcie lub na serwerze lokalnym, na którym działa program SharePoint.

 To okno dialogowe pojawia się, gdy masz opcję wybrania pliku do ustawienia właściwości. To okno dialogowe można otworzyć, wybierając przycisk wielokropka (![ASP.net Mobile Designer](../sharepoint/media/mwellipsis.gif "Wielokropek projektanta ASP.NET Mobile")) obok różnych właściwości w oknie **Właściwości** . Przycisk wielokropka jest również wyświetlany jako monit IntelliSense podczas przypisywania wartości do określonych atrybutów w widoku **źródła** projektanta.

## <a name="uielement-list"></a>Lista elementów UIElement
 **Foldery projektu** Wyświetla listę folderów zdefiniowanych w projekcie lub na serwerze lokalnym, na którym działa program SharePoint. Wybierz przycisk rozwinięcia, aby wyświetlić podfoldery.

 Rozwiń węzeł **projektu** , aby wybrać pliki w projekcie. Aby były wyświetlane jako wybrane w oknie dialogowym, pliki w projekcie muszą spełniać następujące kryteria:

- Plik musi być zawarty w mapowanym folderze.

- Plik należy dodać do pakietu rozwiązania.

- Plik nie może znajdować się w innym projekcie.

  Jeśli chcesz odwołać się do plików, które nie spełniają tych kryteriów, musisz ręcznie wprowadzić ścieżkę do pliku.

  Rozwiń węzeł **serwera** , aby wybrać pliki znajdujące się na serwerze lokalnym, na którym działa program SharePoint. Aby były wyświetlane jako wybrane w oknie dialogowym, te pliki muszą spełniać następujące kryteria:

- Plik musi znajdować się w jednym z następujących mapowanych folderów: **images**, **Layouts** lub **elementy ControlTemplates**.

- Plik nie może znajdować się w bazie danych zawartości programu SharePoint.

  Jeśli chcesz odwołać się do plików, które nie spełniają tych kryteriów, musisz ręcznie wprowadzić ścieżkę do pliku.

  **Zawartość folderu** Wyświetla listę plików w wybranym folderze. Wybierz plik, a następnie wybierz przycisk **OK** , aby zamknąć okno dialogowe i wysłać zaznaczenie do procesu, który go wywołał.

  **Pliki typu** Umożliwia wybranie z listy plików, które są odpowiednie dla wykonywanego zadania.

## <a name="see-also"></a>Zobacz też
- [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Tworzenie kontrolek wielokrotnego użytku dla części sieci Web lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
