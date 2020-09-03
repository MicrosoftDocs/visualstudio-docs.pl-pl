---
title: 'Instrukcje: otwieranie rozwiązań pakietu Office bez uruchamiania kodu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d84515c2c3159b61b96f77555b23eef0df0ae961
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543484"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Instrukcje: otwieranie rozwiązań pakietu Office bez uruchamiania kodu
  Rozwiązanie Microsoft Office utworzone przy użyciu rozszerzeń kodu zarządzanego działa nawet wtedy, gdy ustawienie zabezpieczeń w aplikacji pakietu Office użytkownika końcowego jest ustawione na wartość wysoki. Wynika to z faktu, że zabezpieczenia kodu zestawu .NET są zarządzane przez strukturę Microsoft .NET, a nie przez Microsoft Office.

 Jednak istnieją przypadki, w których można chcieć otworzyć dokument bez uruchamiania kodu. Na przykład kod, który jest uruchamiany, gdy dokument zostanie otwarty, może zmienić zawartość, ale chcesz zaktualizować wygląd dokumentu przed jego zmianą. Możesz też wysłać dokument z określonymi informacjami w nim do kogoś i nie chcesz, aby kod był uruchamiany i prawdopodobnie zmienić jego zawartość.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Istnieje kilka sposobów otwierania dokumentu lub skoroszytu zawierającego rozszerzenia kodu zarządzanego bez uruchamiania kodu zestawu.

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Aby pominąć zestaw przy użyciu klawisza Shift

- Otwórz dokumenty i skoroszyty z menu **plik** , przytrzymując klawisz **SHIFT** , aby uniemożliwić programowi Word i Excel podnoszenie zdarzeń inicjalizacji podczas otwierania dokumentu.

    > [!NOTE]
    > Jeśli otworzysz dokument lub skoroszyt z okienka zadań **wprowadzenie** , wciśnięcie **klawisza Shift** nie spowoduje obejścia kodu. Ponadto wciśnięcie klawisza SHIFT nie zapobiega wywoływaniu zdarzeń po otwarciu dokumentu.

     Ta metoda jest przydatna, jeśli chcesz otworzyć dokument, aby wprowadzić zmiany bez uruchamiania kodu i najpierw zmienić dokument.

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Aby pominąć zestaw przez zmianę jego nazwy lub usunięcie

- Jeśli masz odpowiednie uprawnienia na komputerze, na którym znajduje się zestaw, możesz zmienić nazwę zestawu lub usunąć go, aby dokument lub skoroszyt nie mógł go znaleźć. Powoduje to, że błąd jest zgłaszany za każdym razem, gdy dokument pakietu Office zostanie otwarty.

     Jeśli rozwiązanie jest używane przez wiele osób, ta metoda uniemożliwia działanie rozwiązania dla wszystkich z nich. Może to być przydatne w przypadku znalezienia problemu w kodzie lub serwerze, którego dotyczy odwołanie, i chcesz zatrzymać jego wykonywanie przez wszystkich użytkowników.

## <a name="see-also"></a>Zobacz też
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Aplikacje i manifesty wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
