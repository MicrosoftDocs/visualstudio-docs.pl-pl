---
title: Udzielanie zaufania do dokumentów
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9d245ddf00e4005b763bcd4437d3f8c18d05291e
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986038"
---
# <a name="grant-trust-to-documents"></a>Udzielanie zaufania do dokumentów
  Projekt na poziomie dokumentu ma takie same wymagania dotyczące zabezpieczeń, co projekty na poziomie aplikacji: podpisywanie manifestów przy użyciu certyfikatu lub kliknięcie monitu zaufania. Ponadto dokument lub skoroszyt musi znajdować się w katalogu wyznaczono jako zaufaną lokalizację.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="trusted-locations"></a>Zaufane lokalizacje
 Aplikacje w [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i Office 2010 mają centra zaufania, w których użytkownicy mogą konfigurować ustawienia zabezpieczeń i prywatności, takie jak Zaufane lokalizacje. W przypadku rozwiązań pakietu Office komputer lokalny jest uznawany za zaufaną lokalizację. Jednak ze względu na wyższe ryzyko istnieją pewne katalogi, które nie mogą być zaufane, takie jak foldery tymczasowe systemu, dla każdego użytkownika i dla programu Internet Explorer.

 Aby uzyskać więcej informacji na temat Centrum zaufania, zobacz [zabezpieczenia i zasady oraz ustawienia w pakiecie Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)). Aby uzyskać więcej informacji na temat tworzenia, usuwania i konfigurowania zaufanych folderów oraz zarządzania nimi, zobacz [Konfigurowanie ustawień zaufanych lokalizacji i zaufanych wydawców w systemie 2007 pakietu Office](/previous-versions/office/office-2007-resource-kit/cc178948(v=office.12)) oraz [Tworzenie, usuwanie lub zmienianie zaufanej lokalizacji plików](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

## <a name="security-considerations-for-office-solutions"></a>Zagadnienia dotyczące zabezpieczeń rozwiązań pakietu Office
 Istnieje kilka kwestii związanych z bezpieczeństwem, które należy wziąć pod uwagę, które foldery dodać do zaufanych lokalizacji:

- Foldery lokalne są uważane za bezpieczniejsze i są niejawnie zaufane. Lokalizacje zdalne, takie jak udziały plików, muszą być wyznaczeni jako zaufane lokalizacje.

- Po dodaniu katalogu do zaufanych lokalizacji ta akcja przyznaje pełne zaufanie nie tylko do rozwiązań pakietu Office, ale również do kodu VBA i ActiveX. Z tego powodu katalogu głównego i folderów *Moje dokumenty* nie należy wyznaczyć jako zaufanego.

- Chociaż sam dokument jest zaufany przy użyciu zaufanych lokalizacji, dodatkowe uprawnienia są konieczne do zaufać dostosowaniu. Można udzielić pełnego zaufania do dostosowania przy użyciu podpisywania manifestów z certyfikatem, kliknięcia monitu zaufania lub zainstalowania rozwiązania pakietu Office w katalogu *Program Files* .

- Możesz przechowywać dokument lub skoroszyt rozwiązania poziomu dokumentu w tym samym katalogu, w którym znajduje się zestaw, lub w innym katalogu. Na przykład dokument może znajdować się na serwerze programu SharePoint, a zestaw może znajdować się w sieciowym udziale plików. Aby uzyskać więcej informacji, zobacz [jak: publikowanie rozwiązania Office na poziomie dokumentu na serwerze programu SharePoint przy użyciu technologii ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58).

## <a name="see-also"></a>Zobacz także
- [Udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md)
- [Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-security.md)
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
