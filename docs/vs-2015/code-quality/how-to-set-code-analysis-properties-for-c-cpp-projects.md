---
title: 'Instrukcje: Ustawianie właściwości analizy kodu dla projektów C-C + + | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: b2fb3cb81b49fd4b8cc83e0548110d2025c7488d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277989"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Porady: ustawianie właściwości analizy kodu dla projektów C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można skonfigurować reguły używane przez narzędzie do analizy kodu do analizowania kodu w każdej konfiguracji projektu. Ponadto można skierować analizę kodu, aby pominąć ostrzeżenia z kodu, który został wygenerowany i dodany do projektu przez narzędzie innej firmy.  
  
## <a name="code-analysis-property-page"></a>Strona właściwości analizy kodu  
 Strona właściwości **Analiza kodu** zawiera wszystkie ustawienia konfiguracji analizy kodu dla projektu. Aby otworzyć stronę właściwości Analiza kodu dla projektu w **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Właściwości**. Następnie rozwiń węzeł **Właściwości konfiguracji** i wybierz kartę **Analiza kodu** .  
  
## <a name="project-configuration-and-platform"></a>Konfiguracja i platforma projektu  
 Lista **konfiguracji** i lista **platform** umożliwiają stosowanie różnych ustawień analizy kodu do różnych konfiguracji projektu i kombinacji platform. Na przykład można skierować analizę kodu w celu zastosowania jednego zestawu reguł do projektu na potrzeby kompilacji debugowania i innego zestawu dla kompilacji wydań.  
  
## <a name="enabling-code-analysis"></a>Włączanie analizy kodu  
 Możesz zdecydować, czy włączyć analizę kodu dla projektu, wybierając opcję **Włącz analizę kodu dla C/C++ podczas kompilacji**. W połączeniu z listą **konfiguracji** można na przykład zdecydować, aby wyłączyć analizę kodu dla kompilacji debugowania i włączyć ją dla kompilacji wydań.  
  
 Jeśli projekt zawiera kod zarządzany, możesz zdecydować, czy włączyć lub wyłączyć analizę kodu, wybierając opcję **Włącz analizę kodu podczas kompilacji**.  
  
 Analiza kodu została zaprojektowana w celu ułatwienia poprawy jakości kodu i unikania typowych pułapek. W związku z tym należy uważnie rozważyć, czy należy wyłączyć analizę kodu. Zazwyczaj lepiej jest wyłączyć zestawy reguł lub pojedyncze reguły, które nie mają być stosowane do projektu.  
  
## <a name="generated-code"></a>Wygenerowany kod  
 Deweloperzy często wykorzystują narzędzia, aby szybko opracowywać aplikacje. Narzędzia te mogą generować kod, który jest dodawany do projektu. Warto zapoznać się z naruszeniami reguł, które są wykrywane przez analizę kodu w wygenerowanym kodzie. Nie trzeba jednak ich zobaczyć, jeśli nie chcesz zachować kodu.  
  
 Pole wyboru **Pomiń wyniki z wygenerowanego kodu** na stronie właściwości **Ogólne** umożliwia wybranie, czy mają być wyświetlane ostrzeżenia analizy kodu z kodu zarządzanego, który jest generowany przez narzędzie innej firmy.  
  
## <a name="rule-sets"></a>Zestawy reguł  
 Jeśli projekt zawiera kod zarządzany, możesz wybrać reguły do zastosowania w analizie kodu, wybierając zestaw reguł z listy **Uruchom ten zestaw reguł** .  
  
## <a name="see-also"></a>Zobacz też  
 [Analizowanie jakości kodu zarządzanego](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Analiza kodu dla ostrzeżeń C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)
