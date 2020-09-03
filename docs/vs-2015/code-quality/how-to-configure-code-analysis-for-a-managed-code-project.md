---
title: 'Instrukcje: Konfigurowanie analizy kodu dla projektu kodu zarządzanego | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1ac04a3d8834e3fc24f148fc36327d101e43720a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658849"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Porady: konfigurowanie analizy kodu dla projektu zarządzanego kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] programie [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] [!INCLUDE[vsPro](../includes/vspro-md.md)] można wybrać jedną z listy *zestawów reguł* analizy kodu, która ma zostać zastosowana do projektu kodu zarządzanego. Domyślnym zestawem reguł są reguły zalecane przez firmę Microsoft. Do projektu lub wszystkich projektów w rozwiązaniu można zastosować inny zestaw reguł.

> [!NOTE]
> Informacje o sposobie konfigurowania zestawu reguł dla aplikacji sieci Web ASP.NET można znaleźć w temacie [How to: Configure Code Analysis for a ASP.NET Web Application](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Aby skonfigurować zestaw reguł dla projektu .NET Framework

1. W **Eksplorator rozwiązań**kliknij projekt.

2. W menu **Analizuj** kliknij polecenie **Konfiguruj analizę kodu dla** *ProjectName*.

3. Na listach **Konfiguracja** i **platforma** kliknij konfigurację kompilacji i platformę docelową.

4. Aby uruchomić analizę kodu za każdym razem, gdy projekt jest kompilowany przy użyciu wybranej konfiguracji, zaznacz pole wyboru **Włącz analizę kodu podczas kompilacji (definiuje stałą CODE_ANALYSIS)** . Możesz również ręcznie uruchomić analizę kodu, otwierając menu **Analizuj** i klikając polecenie **Uruchom analizę kodu na** *ProjectName*.

5. Domyślnie Analiza kodu nie raportuje ostrzeżeń z kodu, który jest automatycznie generowany przez narzędzia zewnętrzne. Aby wyświetlić ostrzeżenia z wygenerowanego kodu, wyczyść pole wyboru **Pomiń wyniki z wygenerowanego kodu** .

    > [!NOTE]
    > Ta opcja nie powoduje pomijania błędów analizy kodu i ostrzeżeń z wygenerowanego kodu, gdy błędy i ostrzeżenia pojawiają się w formularzach i szablonach. Można zarówno wyświetlać, jak i konserwować kod źródłowy formularza lub szablonu.

6. Na liście **Uruchom ten zestaw reguł** wykonaj jedną z następujących czynności:

    - Kliknij zestaw reguł, którego chcesz użyć.

    - Kliknij **\<Browse...>** , aby określić istniejący niestandardowy zestaw reguł, którego nie ma na liście.

    - Zdefiniuj niestandardowy zestaw reguł.

         Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych zestawów reguł](../code-quality/creating-custom-code-analysis-rule-sets.md).

## <a name="see-also"></a>Zobacz też
 [Przewodnik: Konfigurowanie niestandardowego zestawu reguł i korzystanie z niego](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
