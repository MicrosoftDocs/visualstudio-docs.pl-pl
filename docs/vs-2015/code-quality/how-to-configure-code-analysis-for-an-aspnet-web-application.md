---
title: 'Instrukcje: Konfigurowanie analizy kodu dla aplikacji sieci Web ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 423264362118343d573b417cd055d2d722df995e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657461"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Porady: konfigurowanie analizy kodu dla aplikacji internetowej ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] i można [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] wybrać opcję z listy *zestawów reguł* analizy kodu, które mają być stosowane do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web. Domyślnym zestawem reguł są reguły zalecane przez firmę Microsoft Mininimum. Możesz wybrać inny zestaw reguł, który ma zostać zastosowany do witryny sieci Web.

### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Aby skonfigurować zestaw reguł dla projektu struktury strony ASP.NET

1. Wybierz witrynę sieci Web w **Eksplorator rozwiązań**.

2. W menu **Analizuj** kliknij polecenie **Konfiguruj analizę kodu dla witryny sieci Web**.

3. Jeśli wybrano rozwiązanie, a rozwiązanie ma więcej niż jeden projekt, wybierz konfigurację i docelowy system operacyjny z list **konfiguracji** i **platformy** .

4. Dla każdego projektu w rozwiązaniu kliknij kolumnę **zestaw reguł** , a następnie kliknij nazwę zestawu reguł do uruchomienia.

5. Domyślnie Analiza kodu jest uruchamiana we wszystkich projektach w rozwiązaniu. Aby wyłączyć lub włączyć analizę kodu dla określonego projektu, wykonaj następujące kroki:

    1. Kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij polecenie Właściwości.

    2. Zaznacz pole wyboru **Włącz analizę kodu** lub usuń jego zaznaczenie. Możesz również ręcznie uruchomić analizę kodu, wybierając opcję **Uruchom analizę kodu w witrynie sieci Web** z menu **Analizuj** .

6. Z listy rozwijanej **Uruchom ten zestaw reguł** wykonaj następujące kroki:

    - Wybierz zestaw reguł, którego chcesz użyć.

    - Wybierz **\<Browse>** , aby określić istniejący niestandardowy zestaw reguł, którego nie ma na liście.

    - Zdefiniuj niestandardowy zestaw reguł. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych zestawów reguł](../code-quality/creating-custom-code-analysis-rule-sets.md).
