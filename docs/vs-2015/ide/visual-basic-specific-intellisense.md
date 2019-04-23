---
title: IntelliSense specyficzne dla języka Visual Basic | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 629683131b93534350439867e41b97ca3bbf3b5a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106881"
---
# <a name="visual-basic-specific-intellisense"></a>IntelliSense specyficzne dla Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor kodu źródłowego języka Visual Basic oferuje następujące funkcje IntelliSense:  
  
- Porady dotyczące składni  
  
     Porady dotyczące składni Wyświetlanie składni instrukcji w miarę wpisywania. To jest przydatne w przypadku instrukcji takich jak [Declare](http://msdn.microsoft.com/library/d3f21fb0-b804-4c99-97ed-583b23894cf1).  
  
## <a name="automatic-completion"></a>Automatyczne uzupełnianie  
  
- Uzupełnianie na różnych słów kluczowych  
  
   Na przykład, jeśli wpiszesz `goto` i spację, funkcję IntelliSense wyświetli listę etykiet zdefiniowanych w menu rozwijanym. Obejmują innych obsługiwanych słów kluczowych `Exit`, `Implements`, `Option`, i `Declare`.  
  
- Uzupełnianie na `Enum` i `Boolean`  
  
   Po instrukcji będzie odnosił się do elementu członkowskiego wyliczenia, IntelliSense wyświetli się lista elementów członkowskich `Enum`. Kiedy oświadczenie będzie odnosił się do `Boolean`, funkcja IntelliSense wyświetli menu rozwijanego PRAWDA / FAŁSZ.  
  
  Uzupełnianie można wyłączyć domyślnie, anulując **automatyczna lista członków** z **ogólne** — strona właściwości w **języka Visual Basic** folderu.  
  
  Można ręcznie wywołać uzupełniania, wywołując listę elementów członkowskich, Dokończ wyraz lub ALT + Strzałka w prawo. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](../ide/using-intellisense.md).  
  
## <a name="intellisense-in-zone"></a>Funkcja IntelliSense w strefie  
 Funkcja IntelliSense w strefie pomaga deweloperom języka Visual Basic, którzy muszą wdrażać aplikacje za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] i są ograniczone do ustawienia częściowej relacji zaufania. Tej funkcji:  
  
- Umożliwia wybranie uprawnień, których aplikacja będzie uruchamiana za pomocą.  
  
- API wyświetlaną w wybranej strefie jako dostępne w listę elementów członkowskich, a następnie Wyświetl interfejsów API, które wymagają dodatkowych uprawnień jako niedostępny.  
  
  Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
