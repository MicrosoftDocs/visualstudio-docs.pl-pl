---
title: Określ nazwę menu Start dla aplikacji ClickOnce
description: Dowiedz się, jak zmienić nazwę wyświetlaną aplikacji ClickOnce przez ustawienie nazwy produktu w oknie dialogowym Opcje publikowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9c9dee27ae78375dcb667bba5157ea84c046073
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940439"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Instrukcje: Określanie nazwy menu Start dla aplikacji ClickOnce
Gdy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja jest zainstalowana zarówno w trybie online, jak i offline, wpis zostanie dodany do menu **Start** i listy **Dodaj lub usuń programy** . Domyślnie nazwa wyświetlana jest taka sama jak nazwa zestawu aplikacji, ale można zmienić nazwę wyświetlaną, ustawiając **nazwę produktu** w oknie dialogowym **Opcje publikacji** .

 **Nazwa produktu** będzie wyświetlana na stronie *publish.htm* ; w przypadku zainstalowanej aplikacji w trybie offline będzie ona nazwą wpisu w menu **Start** i będzie również nazwą wyświetlaną w **aplecie Dodaj lub usuń programy**.

 **Nazwa wydawcy** będzie wyświetlana na stronie *publish.htm* powyżej **nazwy produktu**, a dla zainstalowanej aplikacji w trybie offline będzie również nazwą folderu zawierającego ikonę aplikacji w menu **Start** .

 Skrót menu Start lub odwołanie do aplikacji zostanie utworzone w *%AppData%\Microsoft\Windows\Start start\programy \\<nazwa \> wydawcy*. Skrót lub odwołanie do aplikacji ma taką samą nazwę jak nazwa produktu.

 Możesz ustawić **nazwę produktu** i właściwości **nazwy wydawcy** w oknie dialogowym **Opcje publikowania** dostępne na stronie **Publikuj** w **projektancie projektu**.

### <a name="to-specify-a-start-menu-name"></a>Aby określić nazwę menu Start

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. Kliknij przycisk **Opcje** , aby otworzyć okno dialogowe **Opcje publikowania** .

4. Kliknij pozycję **Opis**.

5. W oknie dialogowym **Opcje publikowania** wprowadź nazwę, która ma być wyświetlana w polu **Nazwa produktu**.

6. Opcjonalnie możesz wprowadzić nazwę wydawcy w polu **nazwa wydawcy**.

## <a name="see-also"></a>Zobacz też
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)