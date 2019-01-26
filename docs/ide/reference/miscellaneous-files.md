---
title: Folder różnych plików
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- builds [Visual Studio], miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], outside of containers
- files [Visual Studio], Miscellaneous Files folder
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2e00e836725620c9a3ded6e2df5119a66d1cb54
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942287"
---
# <a name="miscellaneous-files"></a>Folder różnych plików
Możesz chcieć użyć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] edytorów do wykonywania pracy na plikach z projektem lub rozwiązaniem. Chociaż to rozwiązanie, Otwórz, można otworzyć i zmodyfikować pliki bez dodawania ich do rozwiązania lub projektu. Pliki potrzebne do pracy z niezależnie od kontenery są nazywane różne pliki. Różne pliki są zewnętrzne w stosunku do rozwiązania i projekty nie są uwzględnione w kompilacji i nie może być dołączone rozwiązanie pod kontrolą źródła.

 Otwieranie plików niezależnie z kontenera jest przydatne w przypadku różnych powodów. Może mieć plik, który chcesz wyświetlić podczas opracowywania rozwiązania opartego na projektach, lecz nie jest integralną częścią rozwiązań. Typowe przykłady uwagi dotyczące rozwoju lub instrukcji, schemat bazy danych i klipów kodu. Ponadto możesz chcieć utworzyć autonomiczny plik.

 ![Rozwiązania projekty](../../ide/reference/media/projects_solutions_misc.gif)

 Eksplorator rozwiązań można wyświetlić folder różne pliki, dla plików, gdy są włączone opcje dla folderu. Można ustawić opcji [dokumenty, środowisko, opcje, okno dialogowe](../../ide/reference/documents-environment-options-dialog-box.md). Po zamknięciu dodatkowych plików nie jest skojarzona z danego rozwiązania lub projektu, chyba że jest włączona opcja w tym także.

 Folder różnych plików reprezentuje pliki jako linki. Chociaż ten folder nie jest częścią rozwiązania, po otwarciu rozwiązania, niektóre lub wszystkie z dodatkowych plików, które były otwarte podczas ostatniego zamknięcia rozwiązania są ponownie otwarte, w zależności od ustawień dla folderu.

> [!NOTE]
> Niektóre pliki, które nie pojawiają się w folderze różne pliki to pliki, których nie można zmodyfikować w środowisku IDE, takich jak pliki zip i doc. IDE nie będą śledzić pliki, które mogą być modyfikowane tylko przez edytor zewnętrzny.


## <a name="commands-available-in-the-ide"></a>Poleceń dostępnych w środowisku IDE
 Menu i paski narzędzi, polecenia, które zawierają zmiany na podstawie formatu pliku możesz otworzyć. Po otwarciu pliku tekstowego, na przykład, zostanie wyświetlony pasek narzędzi edytora tekstów i jego polecenia są dostępne. Jeśli następnie otwórz plik schematu XML, zostanie wyświetlony pasek narzędzi schematu XML. Podczas edytowania schematu XML, polecenia paska narzędzi edytora tekstów (lub na pasku narzędzi, sam) są niedostępne. Schemat XML jest aktywnym oknem i jako takie, ma bieżący kontekst zaznaczenia. Podczas przełączania między pliku projektu i inny plik zniknąć wszystkich poleceń związanych z projektem, i tylko te, które są bezpośrednio związane z różnych plików są wyświetlane.

## <a name="folder-display-options"></a>Opcje wyświetlania folderu
 Opcje wyświetlania dodatkowych folderów można ustawić tak, aby folder pojawia się, nawet jeśli nie została jeszcze otwarta różne pliki. Plik rozwiązania nie zarządza trwałe lista dodatkowych plików. Używa opcjonalna funkcja, która umożliwia mu do zapamiętania dla użytkownika ostatnio używanych (MRU) listę plików.

## <a name="see-also"></a>Zobacz też

- [Rozwiązania i projekty](../../ide/solutions-and-projects-in-visual-studio.md)
- [Dokumenty, Środowisko, Opcje — okno dialogowe](../../ide/reference/documents-environment-options-dialog-box.md)