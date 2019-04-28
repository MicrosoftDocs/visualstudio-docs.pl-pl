---
title: 'Instrukcje: Automatyczne ClickOnce zwiększenie wersji publikacji | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: e82d8019a55af9909b4b623622ac8ff52c565dfb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442186"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Instrukcje: Automatyczne zwiększanie wersji publikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas publikowania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikację, zmieniając `Publish Version` właściwości powoduje, że aplikacja opublikowana jako aktualizację. Domyślnie, Visual Studio automatycznie zwiększa `Revision` liczby `Publish Version` każdorazowo, możesz opublikować aplikację.  
  
 To zachowanie można wyłączyć na **Publikuj** strony **projektanta projektu**.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Aby wyłączyć automatyczne zwiększenie wersji publikowania  
  
1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2. Kliknij przycisk **Publikuj** kartę.  
  
3. W **opublikować wersję** sekcji wyczyść **automatycznie zwiększ numer poprawki przy każdym wydaniu** pole wyboru.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: ClickOnce ustawienie wersji publikacji](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
