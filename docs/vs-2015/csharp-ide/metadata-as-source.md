---
title: Metadane jako źródło | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- Go To Definition command
- Code Definition window, viewing metadata as source
- metadata as source [C#]
ms.assetid: 4945a07f-b3be-4f05-a587-fc29058aa8fa
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8d1a4d269b0b7e1afb151bea5bbd97d5ab770d00
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54791052"
---
# <a name="metadata-as-source"></a>Metadane jako źródło
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metadane jako źródło umożliwia wyświetlenie metadanych, który jest wyświetlany jako kod źródłowy języka C# w buforze tylko do odczytu. Dzięki temu widok deklaracji typów i elementów członkowskich (bez implementacji). Można wyświetlić metadane jako źródło, uruchamiając **przejdź do definicji** polecenie, aby uzyskać typy lub elementy członkowskie, których kod źródłowy nie jest dostępna do projektu lub rozwiązania.  
  
> [!NOTE]
>  Jeśli zostanie podjęta próba uruchomienia **przejdź do definicji** polecenia dla typów ani elementów członkowskich, które są oznaczone jako wewnętrzne, zintegrowanego środowiska programistycznego (IDE) nie są wyświetlane metadane jako źródło, niezależnie od tego, czy zestaw odwołujący się jest znajomego, czy nie.  
  
 Można wyświetlić metadane jako źródło w dowolnym edytorze kodu lub **definicji kodu** okna.  
  
## <a name="viewing-metadata-as-source-in-the-code-editor"></a>Podgląd metadanych jako źródła w edytorze kodu  
 Po uruchomieniu **przejdź do definicji** polecenia dla elementu, którego kod źródłowy jest niedostępny, dokument z kartami zawiera widok metadanych tego elementu wyświetlana jako źródło, pojawi się w edytorze kodu. Nazwa typu, a następnie **[z metadanych]**, pojawi się na karcie dokumentu.  
  
 Na przykład jeśli uruchomisz **przejdź do definicji** polecenie, aby uzyskać <xref:System.Console>, metadane <xref:System.Console> pojawi się w edytorze kodu, jak kod źródłowy C# podobny swojej deklaracji, ale bez implementacji.  
  
 ![Metadane jako źródło](../csharp-ide/media/metadatasource.png "MetadataSource")  
  
## <a name="viewing-metadata-as-source-in-the-code-definition-window"></a>Podgląd metadanych jako źródła w oknie definicji kodu  
 Gdy **definicji kodu** okno jest aktywne i widoczne, IDE automatycznie wykonuje **przejdź do definicji** polecenia dla elementów w obszarze kursora w edytorze kodu i elementów, które są wybrane w  **Widok klas** lub **przeglądarka obiektów**. Jeśli kod źródłowy jest niedostępny dla tego elementu, środowisko IDE Wyświetla metadanych elementu jako źródło w **definicji kodu** okna.  
  
 Na przykład, jeśli umieścisz kursor w wyrazie <xref:System.Console> w edytorze kodu, metadane <xref:System.Console> pojawia się jako źródło w **definicji kodu** okna. Źródło przypomina <xref:System.Console> deklaracji, ale bez implementacji.  
  
 Jeśli chcesz zobaczyć deklaracji elementu, który pojawia się w **definicji kodu** okna, kliknij prawym przyciskiem myszy element i kliknij przycisk **przejdź do definicji**.