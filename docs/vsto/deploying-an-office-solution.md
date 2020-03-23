---
title: Wdrażanie rozwiązania pakietu Office
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office applications [Office development in Visual Studio], deploying Office solutions
- Office development in Visual Studio, deploying Office solutions
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- deploying applications [Office development in Visual Studio], Office solutions (2007 system)
- Office development in Visual Studio, troubleshooting
- Office development in Visual Studio, event viewer
- ClickOnce deployment [Office development in Visual Studio], about ClickOnce solution deployments
- Office solutions [Office development in Visual Studio], deploying
- deploying applications [Office development in Visual Studio], troubleshooting
- solutions [Office development in Visual Studio], deploying Office solutions (2007 system)
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24ec10c42935ac961218f910fbef98d51f5f5569
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416513"
---
# <a name="deploy-an-office-solution"></a>Wdrażanie rozwiązania pakietu Office
  Rozwiązania dla pakietu Office można wdrażać za technologii ClickOnce lub Instalatora Windows. Funkcja ClickOnce pozwala zmniejszyć liczbę kroków niezbędnych do wdrożenia i aktualizowania rozwiązania. Z kolei Instalator Windows umożliwia pełną kontrolę nad sposobem instalowania rozwiązania oraz doborem stron wyświetlanych przez instalatora podczas instalacji rozwiązania przez użytkowników.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="deploy-a-solution-by-using-clickonce"></a>Wdrażanie rozwiązania przy użyciu funkcji ClickOnce
 Wdrażanie rozwiązania przy użyciu technologii ClickOnce polega na opublikowaniu go w centralnej lokalizacji, skąd użytkownicy mogą je zainstalować i uruchomić. Rozwiązanie można aktualizować bez konieczności dostarczenia użytkownikom nowego programu instalacyjnego.  Ta opcja wdrażania jest prostsza, ale nie pozwala na przedstawianie użytkownikom stron instalacji niestandardowej. Ponadto rozwiązania trzeba instalować w tylu wystąpieniach, ilu użytkowników korzysta z komputera. Zobacz [Wdrażanie rozwiązania pakietu Office przy użyciu funkcji ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploy-a-solution-by-using-windows-installer"></a>Wdrażanie rozwiązania przy użyciu Instalatora Windows
 Podczas wdrażania rozwiązania przy użyciu Instalatora Windows następuje rozpowszechnienie programu instalacyjnego do użytkowników, którzy następnie sami instalują z niego rozwiązanie. Program instalacyjny może zainstalować rozwiązanie równocześnie dla wszystkich użytkowników komputera, a nie tylko dla bieżącego użytkownika. Oferuje również nieco więcej kontroli nad opcjami wyświetlanymi użytkownikom podczas instalowania rozwiązania. Można na przykład ustawić wyświetlanie umowy licencyjnej albo pozwolić użytkownikom na instalowanie określonych składników rozwiązania. Jednak w przypadku aktualizacji rozwiązania trzeba dostarczyć nowy program instalacyjny. Zobacz [Wdrażanie rozwiązania pakietu Office przy użyciu Instalatora Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="see-also"></a>Zobacz też
- [Bezpieczne rozwiązania pakietu Office](../vsto/securing-office-solutions.md)
- [Wdrażanie rozwiązania pakietu Office przy użyciu funkcji ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Wdrażanie rozwiązania pakietu Office przy użyciu Instalatora Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)
- [Rozwiązywanie problemów z wdrażaniem rozwiązania pakietu Office](../vsto/troubleshooting-office-solution-deployment.md)
