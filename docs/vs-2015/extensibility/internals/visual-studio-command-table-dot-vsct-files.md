---
title: Tabeli poleceń programu Visual Studio (. Pliki Vsct) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a68d9f5dac293cc9048cb4b84aaa487c5079250
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748842"
---
# <a name="visual-studio-command-table-vsct-files"></a>Tabela poleceń programu Visual Studio (pliki Vsct)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Plik konfiguracji tabeli polecenia to plik tekstowy, który opisuje zestaw poleceń, które zawierają pakietu VSPackage. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Polecenia kompilatora tabeli (VSCT) kompiluje pliki konfiguracji w formacie XML (pliki vsct) na pliki wyjściowe (.cto) tabeli polecenie binary. Pliki wynikowe .cto są takie same jak te, które są tworzone za pomocą polecenia kompilatora tabeli (CTC) do kompilowania plików konfiguracyjnych .ctc. Jednak plików oparty na składni XML vsct ma kilka zalet, takie jak XML IntelliSense i edytora XML.  
  
 Aby dowiedzieć się więcej na temat składnia i semantyka .vsct — pliki, zobacz [projektowanie tabeli poleceń XML (. Pliki Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Projektowanie tabeli poleceń XML (pliki Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Opisuje sposób projektowania .vsct — pliki.  
  
 [Instrukcje: tworzenie pliku Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Porównanie metod tworzenia pliku vsct. W tym artykule opisano proces ręcznego tworzenia nowego pliku vsct  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Szczegółowe informacje na temat każdej sekcji w pliku konfiguracji XML tabeli poleceń.  
  
 [Polecenie konfiguracją tabeli (. Pliki CTC)](http://msdn.microsoft.com/en-us/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Przedstawia omówienie .ctc przestarzały format pliku.  
  
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 W tym artykule opisano specyfikacji formatu tabeli poleceń.  
  
 [Zasoby w pakietach VSPackage](../../extensibility/internals/resources-in-vspackages.md)  
 Opisuje sposób używania zarządzane i niezarządzane zasoby w pakietach VSPackage zarządzanych.  
  
 [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Wyjaśnia, jak utworzyć interfejs użytkownika, który zawiera menu, paski narzędzi i pola kombi polecenia.

