---
title: 'Instrukcje: automatyczne zwiększanie wersji publikacji ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 50faf70e8eda6ef7ab01201102540729497eb87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683920"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Porady: automatyczne zwiększenie wersji publikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przypadku publikowania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji zmiana `Publish Version` właściwości powoduje opublikowanie aplikacji jako aktualizacji. Domyślnie program Visual Studio automatycznie zwiększa `Revision` liczbę przy `Publish Version` każdej publikacji aplikacji.  
  
 To zachowanie można wyłączyć na stronie **Publikowanie** **projektanta projektu**.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Aby wyłączyć automatyczne zwiększanie wersji publikacji  
  
1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Kliknij kartę **Publikowanie** .  
  
3. W sekcji **Publikowanie wersji** wyczyść pole wyboru **automatycznie Zwiększ numer poprawki przy każdej wersji** .  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Ustawianie wersji publikacji ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
