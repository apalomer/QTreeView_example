# Data Item
add_library(data_item_widget SHARED QDataItem.cpp )
target_link_libraries(data_item_widget ${QT_LIBRARIES})

# Data item model
QT4_WRAP_CPP(data_item_tree_widget_moc   QDataItemTree.h)
add_library(data_item_tree_widget SHARED QDataItemTree.cpp ${data_item_tree_widget_moc})
target_link_libraries(data_item_tree_widget ${QT_LIBRARIES} data_item_widget)

# Refine calibration
QT4_WRAP_CPP(mainwidget_moc   QMainWidget.h)
QT4_WRAP_UI(mainwidget_ui QMainWidget.ui)
add_library(mainwidget_widget SHARED QMainWidget.cpp ${mainwidget_moc} ${mainwidget_ui} )
target_link_libraries(mainwidget_widget ${QT_LIBRARIES} data_item_tree_widget)
add_executable(QTreeView_example main.cpp)
target_link_libraries(QTreeView_example ${QT_LIBRARIES} mainwidget_widget )
