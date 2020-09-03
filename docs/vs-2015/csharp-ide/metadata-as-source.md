---
title: Metadane jako źródło | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b1d96224be13a12dcaadb394584f8441c7bd1934
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667522"
---
# <a name="metadata-as-source"></a>Metadane jako źródło
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metadane jako źródło umożliwiają wyświetlanie metadanych, które są wyświetlane jako kod źródłowy C# w buforze tylko do odczytu. Umożliwia to wyświetlenie deklaracji typów i członków (bez implementacji). Metadane można wyświetlić jako źródło, uruchamiając polecenie **Przejdź do definicji** dla typów lub elementów członkowskich, których kod źródłowy nie jest dostępny w projekcie lub rozwiązaniu.

> [!NOTE]
> Gdy próbujesz uruchomić polecenie **Przejdź do definicji** dla typów lub elementów członkowskich, które są oznaczone jako wewnętrzne, zintegrowane środowisko programistyczne (IDE) nie wyświetla swoich metadanych jako źródła, niezależnie od tego, czy zestaw, którego dotyczy odwołanie, jest znajomy, czy nie.

 Metadane można wyświetlić jako źródło w edytorze kodu lub w oknie **definicji kodu** .

## <a name="viewing-metadata-as-source-in-the-code-editor"></a>Wyświetlanie metadanych jako źródła w edytorze kodu
 Po uruchomieniu polecenia **Przejdź do definicji** elementu, którego kod źródłowy jest niedostępny, dokument z kartami zawierający widok metadanych tego elementu, wyświetlany jako źródło, pojawia się w edytorze kodu. Nazwa typu, a następnie **[z metadanych]** pojawia się na karcie dokumentu.

 Na przykład, jeśli uruchomisz polecenie **Przejdź do definicji** dla <xref:System.Console> , metadane dla <xref:System.Console> pojawiają się w edytorze kodu jako kod źródłowy C#, który przypomina jego deklarację, ale bez implementacji.

 ![Metadane jako źródło](../csharp-ide/media/metadatasource.png "Źródło danych")

## <a name="viewing-metadata-as-source-in-the-code-definition-window"></a>Wyświetlanie metadanych jako źródła w oknie definicji kodu
 Gdy okno **definicji kodu** jest aktywne lub widoczne, IDE automatycznie wykonuje polecenie **Przejdź do definicji** dla elementów pod kursorem w edytorze kodu oraz dla elementów wybranych w **Widok klasy** lub **Przeglądarka obiektów**. Jeśli kod źródłowy nie jest dostępny dla tego elementu, IDE wyświetla metadane elementu jako źródło w oknie **definicji kodu** .

 Jeśli na przykład umieścisz kursor wewnątrz wyrazu <xref:System.Console> w edytorze kodu, metadane <xref:System.Console> są wyświetlane jako źródło w oknie **definicji kodu** . Źródło przypomina <xref:System.Console> deklarację, ale bez implementacji.

 Jeśli chcesz zobaczyć deklarację elementu, który pojawia się w oknie **definicji kodu** , kliknij prawym przyciskiem myszy element i kliknij polecenie **Przejdź do definicji**.