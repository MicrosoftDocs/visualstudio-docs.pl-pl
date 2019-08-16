---
title: Wdróż rozwiązanie pakietu Office
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
ms.openlocfilehash: abe4951c8ef748231e8c2f0167253caf49fbf1eb
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551595"
---
# <a name="deploy-an-office-solution"></a>Wdróż rozwiązanie pakietu Office
  Rozwiązania dla pakietu Office można wdrażać za technologii ClickOnce lub Instalatora Windows. Funkcja ClickOnce pozwala zmniejszyć liczbę kroków niezbędnych do wdrożenia i aktualizowania rozwiązania. Z kolei Instalator Windows umożliwia pełną kontrolę nad sposobem instalowania rozwiązania oraz doborem stron wyświetlanych przez instalatora podczas instalacji rozwiązania przez użytkowników.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="deploy-a-solution-by-using-clickonce"></a>Wdrażanie rozwiązania przy użyciu technologii ClickOnce
 Wdrażanie rozwiązania przy użyciu technologii ClickOnce polega na opublikowaniu go w centralnej lokalizacji, skąd użytkownicy mogą je zainstalować i uruchomić. Rozwiązanie można aktualizować bez konieczności dostarczenia użytkownikom nowego programu instalacyjnego.  Ta opcja wdrażania jest prostsza, ale nie pozwala na przedstawianie użytkownikom stron instalacji niestandardowej. Ponadto rozwiązania trzeba instalować w tylu wystąpieniach, ilu użytkowników korzysta z komputera. Zobacz [wdrażanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploy-a-solution-by-using-windows-installer"></a>Wdróż rozwiązanie przy użyciu Instalator Windows
 Podczas wdrażania rozwiązania przy użyciu Instalatora Windows następuje rozpowszechnienie programu instalacyjnego do użytkowników, którzy następnie sami instalują z niego rozwiązanie. Program instalacyjny może zainstalować rozwiązanie równocześnie dla wszystkich użytkowników komputera, a nie tylko dla bieżącego użytkownika. Oferuje również nieco więcej kontroli nad opcjami wyświetlanymi użytkownikom podczas instalowania rozwiązania. Można na przykład ustawić wyświetlanie umowy licencyjnej albo pozwolić użytkownikom na instalowanie określonych składników rozwiązania. Jednak w przypadku aktualizacji rozwiązania trzeba dostarczyć nowy program instalacyjny. Zobacz [wdrażanie rozwiązania pakietu Office przy użyciu Instalator Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

## <a name="see-also"></a>Zobacz także
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
- [Wdrażanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Wdróż rozwiązanie pakietu Office przy użyciu Instalator Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md)
- [Rozwiązywanie problemów z wdrażaniem rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-deployment.md)
