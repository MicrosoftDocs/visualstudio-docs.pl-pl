---
title: Zapewnienie automatyzacji dla kodu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd13b7db2065069ff1540dbfc921570c2b230b8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705990"
---
# <a name="providing-automation-for-code"></a>Zapewnianie automatyzacji kodu
Tworzenie modelu automatyzacji dla kodu nie jest wymagane. Zestaw SDK środowiska nie udostępnia próbki w tym celu. Aby uzyskać wgląd w <xref:EnvDTE.CodeModel> modele kodu, zobacz obiekt.

 Aby zaimplementować model kodu, należy zaimplementować wszystkie interfejsy, które są określane przez wewnętrzną strukturę danych. Obiekty muszą pochodzić z `IDispatch` klasy.

 Obiekty, <xref:EnvDTE.CodeModel> które można <xref:EnvDTE.FileCodeModel>rozszerzyć i , <xref:EnvDTE.Project> są dostępne z obiektu i wyglądają następująco:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Można `CodeModel` wybrać do zaimplementowania tylko lub `FileCodeModel` interfejs `Project` <xref:EnvDTE.ProjectItem> w obiekcie, który zwraca z i obiektów. Podaj wszelkie funkcje z tego interfejsu, który jest odpowiedni dla systemu projektu.

 Jeśli chcesz dodać funkcje, takie jak metody lub właściwości, `CodeModel` które `FileCodeModel` nie są dostępne ze standardu i interfejsów, utwórz własny interfejs, który dziedziczy od standardu. Pamiętaj, aby udokumentować go za pomocą systemu projektu, aby użytkownicy końcowi wiedzieli, aby go wyszukać. Zwracasz standardowy interfejs, ale użytkownik `QueryInterface` może wywołać metodę lub rzutować do interfejsu, jeśli wiadomo, że istnieje.

## <a name="see-also"></a>Zobacz też
- [Omówienie modelu automatyzacji](../../extensibility/internals/automation-model-overview.md)
