---
title: Udzielanie zaufania do dokumentów
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5dfa0ad9b27b94c472feabc0e202bd9eee58f08d
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670913"
---
# <a name="grant-trust-to-documents"></a>Udzielanie zaufania do dokumentów
  Projektów dokumentów ma takie same wymagania dotyczące zabezpieczeń, jako projektów na poziomie aplikacji: podpisywanie manifestów za pomocą certyfikatu lub klikając monit o udzielenie zaufania. Ponadto dokument lub skoroszyt musi znajdować się w katalogu, który jest wyznaczone jako zaufaną lokalizację.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="trusted-locations"></a>Zaufane lokalizacje  
 Aplikacje w [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i Office 2010 mają centra zaufania, której użytkownicy mogą skonfigurować ustawienia zabezpieczeń i prywatności, takie jak zaufanych lokalizacji. Dla rozwiązań pakietu Office komputer lokalny jest uznawany za zaufanej lokalizacji. Jednak ze względu na większe ryzyko, istnieją niektóre katalogi, które nigdy nie może być zaufanych, takich jak foldery tymczasowe systemu dla każdego użytkownika i programu Internet Explorer.  
  
 Aby uzyskać więcej informacji na temat Centrum zaufania Zobacz [i zasady ustawień zabezpieczeń i w pakiecie Office 2010](http://go.microsoft.com/fwlink/?LinkId=89202). Aby uzyskać więcej informacji o sposobie tworzenia, zarządzania, Usuń i Konfigurowanie zaufanych folderów, zobacz [skonfiguruj zaufane lokalizacje i ustawienia zaufanych wydawców w 2007 Office system](http://go.microsoft.com/fwlink/?LinkId=89203) i [Utwórz, usuń lub zmień zaufanej lokalizacji plików](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="security-considerations-for-office-solutions"></a>Zagadnienia dotyczące zabezpieczeń rozwiązań pakietu Office  
 Istnieje kilka obawy związane z bezpieczeństwem, po zastanowieniu się nad foldery, które można dodać do zaufanych lokalizacji:  
  
-   Foldery lokalne są traktowane jako więcej bezpieczna i są niejawnie zaufane. Lokalizacjach zdalnych, takich jak udziały plików muszą być wyznaczone jako zaufanych lokalizacji.  
  
-   Po dodaniu katalogu do zaufanej lokalizacji, ta akcja spowoduje przyznanie pełnego zaufania nie tylko do rozwiązań pakietu Office, ale do kodu VBA i ActiveX. Z tego powodu, katalog główny i *Moje dokumenty* folderów nie powinno być wyznaczone jako zaufane.  
  
-   Mimo że samego dokumentu jest zaufany, korzystając z zaufanej lokalizacji, ufać dostosowania są wymagane dodatkowe uprawnienia. Można przyznać pełne zaufanie do dostosowania przy użyciu podpisywanie manifestów za pomocą certyfikatu, klikając monit o udzielenie zaufania lub instalowanie rozwiązania dla pakietu Office do *Program Files* katalogu.  
  
-   W tym samym katalogu co zestaw lub w innym katalogu może przechowywać na dokument lub skoroszyt to rozwiązanie na poziomie dokumentu. Na przykład dokument może znajdować się na serwerze programu SharePoint i zestaw może znajdować się w sieciowym udziale plików. Aby uzyskać więcej informacji, zobacz [porady: publikowanie rozwiązania pakietu Office poziomu dokumentu na serwerze programu SharePoint przy użyciu technologii ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## <a name="see-also"></a>Zobacz także  
 [Udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md)   
 [Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-security.md)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)  
  
  