---
title: Kodowania i linie podziału | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 88f04720610bad5064f7f9d7a43beef2410b045f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54787469"
---
# <a name="encodings-and-line-breaks"></a>Kodowania i linie podziału
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można używać **pliku/zaawansowane opcje zapisywania** ma ustawienia, aby określić typ podział wiersza znakami możesz. Można również zmienić kodowanie pliku przy użyciu tych samych ustawień.  
  
> [!NOTE]
>  W przypadku niektórych typów ustawień środowiska deweloperskiego (Visual Basic F#, tworzenie aplikacji sieci Web) mogą nie być widoczne **zaawansowane opcje zapisywania** w menu. Aby zmienić swoje ustawienia (na przykład aby ogólne), otwórz **narzędzia / Import i eksport ustawień**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 W programie Visual Studio, następujące znaki są interpretowane jako podziały wierszy:  
  
- CRLF: Znaku powrotu karetki i wysuwu wiersza Unicode znaki 000 D + 000A  
  
- LF: Znak nowego wiersza, Unicode 000A  
  
- NEL: Następny wiersz, znaków Unicode 0085  
  
- LS: Separator wiersza, znaków Unicode 2028  
  
- PS: Separator akapitu, znaków Unicode 2029  
  
  Tekst, który jest kopiowany z innych aplikacji zachowuje oryginalne kodowanie i znaki podziału wiersza. Na przykład po Kopiuj tekst ze Schowka i wklej go do pliku tekstowego w programie Visual Studio tekst ma tych samych ustawień, których go w Notatniku.  
  
  Po otwarciu pliku, który zawiera znaki podziału wiersza w innej, zobaczysz okno dialogowe z pytaniem, czy znaki podziału wiersza niespójne powinny być znormalizowane i jakiego typu podziałów wiersza, aby wybrać.
