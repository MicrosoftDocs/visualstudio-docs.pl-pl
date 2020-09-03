---
title: Fragmenty kodu XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bc8946d62f47291a6e0e3f26032589bfdf0de16
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669362"
---
# <a name="xml-snippets"></a>Fragmenty kodu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor XML oferuje funkcję, nazywaną *fragmentami kodu XML*, która umożliwia szybsze tworzenie plików XML. Można ponownie użyć fragmentów kodu XML, wstawiając je do plików. Możesz również generować dane XML na podstawie schematu definicji schematu XML (XSD).

## <a name="reusable-xml-snippets"></a>Fragmenty kodu XML wielokrotnego użytku
 Edytor XML zawiera wiele fragmentów kodu, które obejmują niektóre typowe zadania. Dzięki temu można łatwiej tworzyć pliki XML. Na przykład jeśli tworzysz schemat XML przy użyciu fragmentów "element sekwencji typu złożonego" i "element typu prostego", wstawi następujący tekst XML do pliku. Następnie należy zmienić `name` wartość tak, aby odpowiadała Twoim potrzebom.

```
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

 Fragmenty kodu można wstawiać na dwa sposoby. Polecenie **Wstaw fragment** kodu wstawia fragment kodu XML w pozycji kursora. Element **przestrzenny z** poleceniem otacza fragment kodu XML wokół zaznaczonego tekstu. Oba polecenia są dostępne w podmenu **IntelliSense** w menu **Edycja** lub w menu skrótów edytora.

 Aby uzyskać więcej informacji, zobacz [How to: Use XML defragments](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Fragmenty kodu XML generowane przez schemat
 Edytor XML umożliwia również generowanie fragmentu kodu XML na podstawie schematu XML. Ta funkcja umożliwia wypełnienie elementu elementami XML wygenerowanymi na podstawie informacji o schemacie dla tego elementu.

 Aby uzyskać więcej informacji, zobacz [jak: generować fragment kodu XML ze schematu XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Utwórz nowe fragmenty kodu XML
 Oprócz fragmentów kodu, które są domyślnie dołączone do [!INCLUDE[msCoName](../includes/msconame-md.md)] programu Visual Studio, można również tworzyć własne fragmenty kodu XML i korzystać z nich.

 Aby uzyskać więcej informacji, zobacz [How to: Create XML defragments](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Zobacz też
 [Edytor XML](../xml-tools/xml-editor.md)
