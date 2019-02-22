---
title: Tworzenie wystąpień projektów przy użyciu fabryk projektów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3680af73c281a01a7938805f859e0ff88c1ba44
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641237"
---
# <a name="create-project-instances-by-using-project-factories"></a>Tworzenie wystąpień projektów przy użyciu fabryk projektów
Typów projektów w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] użyj *fabryka projektu* do tworzenia wystąpień obiektów projektu. Fabryka projektu jest podobna do fabryki klas standard dla obiektów COM, cocreatable. Obiekty projektu nie są jednak cocreatable; mogą one można tworzyć tylko za pomocą fabryki projektu.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE wywołuje fabryka projektu zaimplementowane w swojej pakietu VSPackage, gdy użytkownik wczytuje istniejący projekt lub tworzy nowy projekt w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Nowy obiekt projektu zapewnia środowisko IDE z wystarczającą ilość informacji, aby wypełnić **Eksploratora rozwiązań**. Nowy obiekt projektu także interfejsami wymaganymi do obsługi wszystkich odpowiednich akcji UI inicjowane przez środowisko IDE.

 Możesz zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfejsu w klasie w projekcie. Zazwyczaj znajduje się w module swój własny.

 Projekty, które obsługuje Agregacja przez właściciela, muszą zostać zachowane klawiszem właściciela w pliku projektu. Gdy <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> metoda jest wywoływana w projekcie przy użyciu klucza właściciela, należących do projektu konwertuje jego właściciela klucza fabryką projektu, następnie wywołuje GUID `CreateProject` metody w tej fabryce projektu w celu utworzenia rzeczywistych.

## <a name="create-an-owned-project"></a>Tworzenie projektu należące do firmy
 Właściciel tworzy projekt należące do firmy w dwóch fazach:

1. Przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> metody. Zapewnia możliwość tworzenia obiektu projektu zagregowane oparte na danych wejściowych kontrolowanie należących do projektu `IUnknown`. Należących do projektu przekazuje wewnętrzny `IUnknown` i zagregowane obiekt do projektu właściciela. Daje możliwość przechowywania wewnętrzny należących do projektu `IUnknown`.

2. Przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> metody. Należących do projektu nie wszystkie jego wystąpienia, gdy ta metoda jest wywoływana zamiast wywoływać metodę `IVsProjectFactory::CreateProject` tak jak w przypadku projektów, które nie należą do. Dane wejściowe `VSOWNEDPROJECTOBJECT` wyliczenie jest zazwyczaj zagregowane należących do projektu. Należących do projektu, można użyć tej zmiennej do określenia, czy jego obiektu projektu już istnieje (plik cookie nie jest równa NULL) lub musi zostać utworzona (plik cookie jest równa NULL).

   Typy projektów są identyfikowane przez projekt Unikatowy identyfikator GUID, podobnie jak identyfikator CLSID cocreatable obiektu COM. Zazwyczaj jeden projekt fabryka obsługuje tworzenia wystąpień typu pojedynczego projektu, mimo że można mieć jedną fabryka projektu obsługiwać więcej niż jeden identyfikator GUID typu projektu.

   Typy projektów są skojarzone z rozszerzeniem nazwy pliku określonej. Po użytkownik próbuje otworzyć istniejący plik projektu lub podejmuje próbę utworzenia nowego projektu przez Sklonowanie szablonu, IDE używa rozszerzenia w pliku w celu określenia odpowiedniego identyfikatora GUID projektu.

   Jak najszybciej IDE ustala, czy należy utworzyć nowy projekt lub Otwórz istniejący projekt określonego typu, IDE używa informacji w kluczu rejestru systemu **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]**  można znaleźć którego pakietu VSPackage implementuje fabryki wymagane projekty. IDE ładuje tego pakietu VSPackage. W <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metody pakietu VSPackage należy zarejestrować jego fabryka projektu środowiska IDE, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> metody.

   Podstawową metodą `IVsProjectFactory` interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, która powinna obsługiwać dwa scenariusze: otwierania istniejącego projektu i tworzenia nowego projektu. Większość projektów przechowywania ich stanu projektu w pliku projektu. Zazwyczaj nowe projekty są tworzone przez tworzenie kopii pliku szablonu jest przekazywany do `CreateProject` metody, a następnie otwarcie kopii. Istniejące projekty są tworzone przez bezpośrednio, otwierając plik projektu przekazany do `CreateProject` metody. `CreateProject` Metoda można wyświetlić dodatkowe funkcje interfejsu użytkownika dla użytkownika, zgodnie z potrzebami.

   Projekt można również użyć żadne pliki, a zamiast tego należy przechowywać stanu projektu w mechanizm magazynu innego niż system plików, takich jak bazy danych lub serwer sieci Web. W tym przypadku parametr nazwy pliku jest przekazywane do `CreateProject` metoda nie jest faktycznie ścieżka systemu plików, ale unikatowy ciąg — adres URL — do identyfikowania danych projektu. Nie należy skopiować pliki szablonów, które są przekazywane do `CreateProject` do wyzwolenia sekwencji konstrukcji odpowiednie do wykonania.

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)