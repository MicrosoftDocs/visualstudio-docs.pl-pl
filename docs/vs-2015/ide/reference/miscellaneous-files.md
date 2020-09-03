---
title: Różne pliki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8dc11714fc8b2d5a345d94ddfe4c5de2c2cd7fe5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666852"
---
# <a name="miscellaneous-files"></a>Folder różnych plików
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Możesz chcieć użyć [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] edytorów do pracy niezależnie od plików z projektu lub rozwiązania. Gdy masz otwarte rozwiązanie, możesz otwierać i modyfikować pliki bez dodawania ich do rozwiązania lub do projektu. Pliki, z którymi chcesz współpracować niezależnie od kontenerów, są nazywane różnymi plikami. Różne pliki są zewnętrzne dla rozwiązań i projektów, nie są uwzględniane w kompilacjach i nie mogą być dołączone do rozwiązania pod kontrolą źródła.

 Otwieranie plików niezależnie od kontenera jest przydatne z różnych powodów. Może istnieć plik, który ma być wyświetlany podczas opracowywania rozwiązań opartych na projekcie, ale nie jest integralną częścią opracowywania rozwiązania. Typowe przykłady obejmują uwagi dotyczące programowania lub instrukcje, schemat bazy danych i klipy kodu. Ponadto możesz chcieć utworzyć plik autonomiczny.

 ![Projekty rozwiązań](../../ide/reference/media/projects-solutions-misc.gif "Projects_Solutions_Misc")

 Jeśli opcje dla tego folderu są włączone, Eksplorator rozwiązań może wyświetlić folder różne pliki. Opcje można ustawić za pomocą [okna dialogowego dokumenty, środowisko, opcje](../../ide/reference/documents-environment-options-dialog-box.md). Po zamknięciu różnego pliku nie jest on kojarzony z żadnym konkretnym rozwiązaniem lub projektem, chyba że jest ona również włączona.

 Folder różne pliki reprezentuje pliki jako linki. Mimo że ten folder nie jest częścią rozwiązania, podczas otwierania rozwiązania niektóre lub wszystkie inne pliki, które zostały otwarte, gdy rozwiązanie zostało ostatnio zamknięte, są ponownie otwierane, w zależności od ustawień dla tego folderu.

> [!NOTE]
> Niektóre pliki, które nie są wyświetlane w folderze różne pliki, to pliki, których nie można modyfikować w środowisku IDE, takie jak pliki zip i pliki. doc. IDE nie śledzi plików, które mogą być modyfikowane tylko za pomocą zewnętrznego edytora.

## <a name="commands-available-in-the-ide"></a>Polecenia dostępne w środowisku IDE
 Menu, paski narzędzi i polecenia, które zawierają zmiany, na podstawie formatu otwartego pliku. Gdy otworzysz plik tekstowy, pojawi się pasek narzędzi Edytor tekstu, a jego polecenia są dostępne. Jeśli następnie otworzysz plik schematu XML, pojawi się pasek narzędzi schematu XML. Podczas edytowania schematu XML polecenia paska narzędzi edytora tekstu (lub samego paska narzędzi) są niedostępne. Schemat XML jest aktywnym oknem i w związku z tym ma bieżący kontekst zaznaczenia. Po przełączeniu między plikiem projektu a plikiem różne, wszystkie polecenia związane z projektem znikają i są wyświetlane tylko te, które są bezpośrednio powiązane z plikiem różne.

## <a name="folder-display-options"></a>Opcje wyświetlania folderu
 Można ustawić opcje wyświetlania dla folderu różne, aby folder pojawił się, mimo że nie zostały otwarte żadne różne pliki. Plik rozwiązania nie umożliwia trwałego zarządzania listą różnych plików. Korzysta ona z funkcji opcjonalnej, która pozwala na zapamiętanie listy plików ostatnio używanych (MRU) dla użytkownika.

## <a name="see-also"></a>Zobacz też
 [Rozwiązania i projekty](../../ide/solutions-and-projects-in-visual-studio.md) [dokumenty, środowisko, Opcje — okno dialogowe](../../ide/reference/documents-environment-options-dialog-box.md)
