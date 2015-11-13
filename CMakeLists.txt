project(lc NONE)
include(UseLATEX.cmake)

set(root_name lc)
set(latex_file ${root_name}.tex)
set(bibtex_file ${root_name}.bib)
set(pdf_file ${root_name}.pdf)

set(images 
    images/an_image.pdf
    )
add_latex_document(${latex_file} 
    BIBFILES ${bibtex_file} 
    CONFIGURE ${latex_file}
    IMAGES ${images}
    )

add_custom_target(tar_gz ALL
    tar cvzf lc.tar.gz ${latex_file} ${bibtex_file} ${pdf_file} ${images}
    DEPENDS ${latex_file} ${bibtex_file} ${pdf_file} ${images}
    COMMENT "Bundling all files (tar.gz)"
    VERBATIM)

add_custom_target(zip ALL
    zip lc ${latex_file} ${bibtex_file} ${pdf_file} ${images}
    DEPENDS ${latex_file} ${bibtex_file} ${pdf_file} ${images}
    COMMENT "Bundling all files (zip)"
    VERBATIM)

