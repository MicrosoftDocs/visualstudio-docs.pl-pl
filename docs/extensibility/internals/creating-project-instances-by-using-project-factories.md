---
title: Tworzenie wystąpień projektu przy użyciu fabryk projektu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31ba5dd11af18f8a723b2271544eff2bd292e2e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709061"
---
# <a name="create-project-instances-by-using-project-factories"></a>Tworzenie wystąpień projektu przy użyciu fabryk projektów
Typy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektów w użyciu *fabryki projektu* do tworzenia wystąpień obiektów projektu. Fabryka projektów jest podobna do standardowej fabryki klas dla współużytkowanych obiektów COM. Jednak obiekty projektu nie są współtwórczym; mogą być tworzone tylko przy użyciu fabryki projektów.

 IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wywołuje fabrykę projektu zaimplementowane w vsPackage, gdy użytkownik ładuje istniejący projekt lub tworzy nowy projekt w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Nowy obiekt projektu dostarcza IDE wystarczającej ilości informacji do wypełniania **Eksploratora rozwiązań.** Nowy obiekt projektu udostępnia również interfejsy wymagane do obsługi wszystkich odpowiednich akcji interfejsu użytkownika zainicjowanych przez IDE.

 Interfejs można <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> zaimplementować w klasie w projekcie. Zazwyczaj znajduje się w swoim własnym module.

 Projekty, które obsługują są agregowane przez właściciela musi utrwalić klucz właściciela w pliku projektu. Gdy <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> metoda jest wywoływana w projekcie z kluczem właściciela, posiadany projekt konwertuje `CreateProject` jego klucz właściciela do identyfikatora GUID fabryki projektu, a następnie wywołuje metodę w tej fabryce projektu, aby wykonać rzeczywiste tworzenie.

## <a name="create-an-owned-project"></a>Tworzenie projektu będącego własnością
 Właściciel tworzy posiadany projekt w dwóch etapach:

1. Wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> metodę. Daje to posiadanym projektowi możliwość utworzenia zagregowanego `IUnknown`obiektu projektu na podstawie kontroli danych wejściowych. Posiadany projekt przekazuje `IUnknown` wewnętrzny i zagregowany obiekt z powrotem do projektu właściciela. Daje to posiadanym projektowi szansę `IUnknown`na przechowywanie wewnętrznego .

2. Wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> metodę. Posiadany projekt wykonuje wszystkie jego wystąpienia, gdy ta `IVsProjectFactory::CreateProject` metoda jest wywoływana zamiast wywoływania, jak byłoby w przypadku projektów, które nie są własnością. Wyliczenie danych wejściowych `VSOWNEDPROJECTOBJECT` jest zazwyczaj zagregowanym własnością projektu. Posiadany projekt może użyć tej zmiennej, aby ustalić, czy jego obiekt projektu został już utworzony (plik cookie nie ma równej wartości NULL) lub musi zostać utworzony (plik cookie jest równy NULL).

   Typy projektów są identyfikowane przez unikatowy identyfikator GUID projektu, podobny do identyfikatora CLSID współtworzonego obiektu COM. Zazwyczaj jedna fabryka projektu obsługuje tworzenie wystąpień pojedynczego typu projektu, chociaż możliwe jest, że jedna fabryka projektu obsługuje więcej niż jeden identyfikator GUID typu projektu.

   Typy projektów są skojarzone z rozszerzeniem nazwy określonego pliku. Gdy użytkownik próbuje otworzyć istniejący plik projektu lub próbuje utworzyć nowy projekt przez klonowanie szablonu, IDE używa rozszerzenia w pliku do określenia odpowiedniego identyfikatora GUID projektu.

   Jak tylko IDE określa, czy należy utworzyć nowy projekt lub otworzyć istniejący projekt określonego typu, IDE używa informacji w rejestrze systemu w obszarze **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects],** aby znaleźć, który vspackage implementuje wymaganą fabrykę projektu. IDE ładuje ten VSPackage. W <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodzie VSPackage musi zarejestrować swoją fabrykę <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> projektu z IDE, wywołując metodę.

   Podstawową metodą `IVsProjectFactory` interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>jest , który powinien obsługiwać dwa scenariusze: otwarcie istniejącego projektu i utworzenie nowego projektu. Większość projektów przechowuje swój stan projektu w pliku projektu. Zazwyczaj nowe projekty są tworzone przez wykonanie kopii pliku `CreateProject` szablonu przekazane do metody, a następnie otwarcie kopii. Istniejące projekty są tworzone przez bezpośrednie otwarcie pliku `CreateProject` projektu przekazanego do metody. Metoda `CreateProject` może wyświetlać dodatkowe funkcje interfejsu użytkownika dla użytkownika w razie potrzeby.

   Projekt może również używać żadnych plików, a zamiast tego przechowywać swój stan projektu w mechanizmie magazynowania innym niż system plików, takim jak baza danych lub serwer sieci Web. W takim przypadku parametr nazwy pliku `CreateProject` przekazany do metody nie jest w rzeczywistości ścieżką systemu plików, ale unikatowym ciągiem — adresem URL — służącym do identyfikowania danych projektu. Nie trzeba kopiować plików szablonów, `CreateProject` które są przekazywane do wyzwalania odpowiedniej sekwencji konstrukcji do wykonania.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
