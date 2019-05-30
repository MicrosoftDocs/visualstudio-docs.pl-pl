---
title: Omówienie rozwiązań
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9405177e193349eeb6e7767b70af0ef82208cc4c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322595"
---
# <a name="solutions-overview"></a>Omówienie rozwiązań

Rozwiązanie to grupa jeden lub więcej projektów, które współpracują ze sobą, aby utworzyć aplikację. Informacje o projekcie i stanie odnoszących się do rozwiązania są przechowywane w dwóch plikach innego rozwiązania. [Plik rozwiązania (.sln)](solution-dot-sln-file.md) jest oparte na tekście umieszczone pod kontrolą kodu źródłowego i udostępniana między użytkownikami i. [Plik opcji (suo) użytkownika rozwiązania](solution-user-options-dot-suo-file.md) jest plikiem binarnym. Co w efekcie plik .suo nie można umieścić pod kontrolą kodu źródłowego i zawiera informacje specyficzne dla użytkownika.

Dowolnego pakietu VSPackage można zapisać do dowolnego typu pliku rozwiązania. Ze względu na charakter pliki istnieją dwa różne interfejsy implementowane był na nich zapis. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> Interfejsu zapisuje informacje tekstowe do pliku .sln i <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfejsu zapisuje plik .suo strumieni binarnych.

> [!NOTE]
> Projekt nie ma jawnie zapisu wykorzystywany do pliku rozwiązania. środowisko sobie z nimi poradzi dla projektu. W związku z tym chyba że chcesz dodać dodatkową zawartość do pliku rozwiązania, nie trzeba zarejestrować Twojego pakietu VSPackage w ten sposób.

Każdego pakietu VSPackage obsługi trwałości rozwiązanie używa trzech interfejsów <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfejs, który jest implementowany przez środowisko i wywoływany przez pakietu VSPackage, i `IVsPersistSolutionProps` i `IVsPersistSolutionOpts`, które są zarówno implementowane przez pakietu VSPackage. `IVsPersistSolutionOpts` Interfejsu tylko musi zostać wdrożone, jeśli ma on zostać zapisany przez pakietu VSPackage plik .suo informacje prywatne.

Po otwarciu rozwiązania odbywa się następujący proces.

1. Środowisko odczytuje rozwiązania.

2. Jeśli znajdzie środowiska `CLSID`, ładuje odpowiedniego pakietu VSPackage.

3. Jeśli pakietu VSPackage jest ładowany, wywołania środowiska `QueryInterface` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interfejsu dla interfejsu, który wymaga pakietu VSPackage.

   - Podczas odczytu z pliku SLN, środowisko wywołuje `QueryInterface` dla `IVsPersistSolutionProps`.

   - Podczas odczytywania z pliku .suo, środowisko wywołuje `QueryInterface` dla `IVsPersistSolutionOpts`.

   Szczegółowe informacje dotyczące korzystania z tych plików można znaleźć w [rozwiązania (. Plik sln)](../../extensibility/internals/solution-dot-sln-file.md) i [opcje użytkownika rozwiązania (. Plik suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Jeśli chcesz utworzyć nową konfigurację rozwiązania składający się z dwóch projektów konfiguracje z wyłączeniem trzecią z kompilacji, należy użyć interfejsu użytkownika strony właściwości lub automatyzacji. Nie można zmienić konfiguracji Menedżera kompilacji rozwiązania i ich właściwości bezpośrednio, ale można manipulować Menedżera kompilacji rozwiązania przy użyciu `SolutionBuild` klasy z obiektu DTE w modelu automatyzacji. Aby uzyskać więcej informacji na temat konfigurowania rozwiązania, zobacz [konfiguracji rozwiązania](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>