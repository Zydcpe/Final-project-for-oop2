# Final-project-for-oop2
import sys
from PyQt6.QtWidgets import (
    QApplication, QMainWindow, QWidget, QLabel,
    QPushButton, QVBoxLayout, QLineEdit, QMessageBox
)
from PyQt6.QtCore import Qt


class WelcomePage(QMainWindow):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("LeptoTrack | Welcome")
        self.setMinimumSize(760, 520)
        self.resize(950, 620)

        # Create the main page
        page = QWidget()
        self.setCentralWidget(page)

        layout = QVBoxLayout(page)
        layout.setContentsMargins(50, 35, 50, 35)
        layout.setSpacing(18)

        layout.addStretch()

        # Logo
        logo = QLabel("✚")
        logo.setAlignment(Qt.AlignmentFlag.AlignCenter)
        layout.addWidget(logo)

        # Hospital name
        hospital_label = QLabel("Enter Hospital Name:")
        hospital_label.setAlignment(Qt.AlignmentFlag.AlignCenter)
        layout.addWidget(hospital_label)

        # Input for hospital name
        self.hospital_input = QLineEdit()
        self.hospital_input.setPlaceholderText("Type hospital name here...")
        self.hospital_input.setMinimumWidth(320)
        self.hospital_input.setAlignment(Qt.AlignmentFlag.AlignCenter)

        layout.addWidget(
            self.hospital_input,
            alignment=Qt.AlignmentFlag.AlignCenter
        )

        # Title
        title = QLabel("LeptoTrack")
        title.setAlignment(Qt.AlignmentFlag.AlignCenter)
        layout.addWidget(title)

        # Description
        description = QLabel(
            "Single-Hospital Leptospirosis Monitoring System"
        )
        description.setAlignment(Qt.AlignmentFlag.AlignCenter)
        layout.addWidget(description)

        # Open button
        open_button = QPushButton("Open Monitoring Dashboard")
        open_button.clicked.connect(self.open_dashboard)
        layout.addWidget(
            open_button,
            alignment=Qt.AlignmentFlag.AlignCenter
        )

        layout.addStretch()

        # Footer
        footer = QLabel("Hospital Monitoring • LeptoTrack")
        footer.setAlignment(Qt.AlignmentFlag.AlignCenter)
        layout.addWidget(footer)

    def open_dashboard(self):
        hospital_name = self.hospital_input.text().strip()

        if hospital_name == "":
            QMessageBox.warning(
                self,
                "Warning",
                "Please enter the hospital name first."
            )
            return

        QMessageBox.information(
            self,
            "Welcome",
            "Hospital name successfully entered!"
        )


app = QApplication(sys.argv)
window = WelcomePage()
window.show()
sys.exit(app.exec())
