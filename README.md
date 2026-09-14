Preview:
![Hasil Run StudentProfile](screenshots/Screenshot_20260914_225744.png)

Kode:
```kotlin
package com.example.studentprofile

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.activity.enableEdgeToEdge
import androidx.compose.foundation.Image
import androidx.compose.foundation.background
import androidx.compose.foundation.layout.Arrangement
import androidx.compose.foundation.layout.Box
import androidx.compose.foundation.layout.Column
import androidx.compose.foundation.layout.Row
import androidx.compose.foundation.layout.Spacer
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.foundation.layout.fillMaxWidth
import androidx.compose.foundation.layout.height
import androidx.compose.foundation.layout.padding
import androidx.compose.foundation.layout.size
import androidx.compose.foundation.layout.width
import androidx.compose.foundation.shape.CircleShape
import androidx.compose.foundation.shape.RoundedCornerShape
import androidx.compose.material.icons.Icons
import androidx.compose.material.icons.automirrored.filled.MenuBook
import androidx.compose.material.icons.filled.CalendarMonth
import androidx.compose.material.icons.filled.Email
import androidx.compose.material.icons.filled.Groups
import androidx.compose.material.icons.filled.Person
import androidx.compose.material.icons.filled.Place
import androidx.compose.material.icons.filled.School
import androidx.compose.material3.Card
import androidx.compose.material3.CardDefaults
import androidx.compose.material3.HorizontalDivider
import androidx.compose.material3.Scaffold
import androidx.compose.material3.Text
import androidx.compose.material3.VerticalDivider
import androidx.compose.runtime.Composable
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.draw.clip
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.graphics.vector.ImageVector
import androidx.compose.ui.layout.ContentScale
import androidx.compose.ui.res.painterResource
import androidx.compose.ui.text.font.FontWeight
import androidx.compose.ui.unit.dp
import androidx.compose.ui.unit.sp
import com.example.studentprofile.ui.theme.StudentProfileTheme

private val PrimaryBlue = Color(0xFF0056C6)
private val BackgroundColor = Color(0xFFF3F4F6)
private val DarkBlueText = Color(0xFF0D253F)
private val IconBgColor = Color(0xFFE8F1FF)
private val DividerColor = Color(0xFFE5E7EB)
private val TextGray = Color(0xFF6B7280)

class MainActivity : ComponentActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()

        setContent {
            StudentProfileTheme {
                Scaffold(
                    modifier = Modifier.fillMaxSize()
                ) { innerPadding ->
                    StudentProfileScreen(
                        modifier = Modifier.padding(innerPadding)
                    )
                }
            }
        }
    }
}

@Composable
fun StudentProfileScreen(modifier: Modifier = Modifier) {

    Box(
        modifier = modifier
            .fillMaxSize()
            .background(BackgroundColor)
    ) {

        // Header
        Box(
            modifier = Modifier
                .fillMaxWidth()
                .height(220.dp)
                .background(PrimaryBlue)
                .padding(24.dp),
            contentAlignment = Alignment.TopCenter
        ) {
            Text(
                text = "STUDENT PROFILE",
                color = Color.White,
                fontSize = 24.sp,
                fontWeight = FontWeight.Bold
            )
        }

        // Main Card
        Card(
            modifier = Modifier
                .fillMaxWidth()
                .padding(
                    start = 20.dp,
                    end = 20.dp,
                    top = 90.dp,
                    bottom = 24.dp
                ),
            shape = RoundedCornerShape(24.dp),
            colors = CardDefaults.cardColors(
                containerColor = Color.White
            ),
            elevation = CardDefaults.cardElevation(
                defaultElevation = 6.dp
            )
        ) {
            ProfileContent()
        }
    }
}

@Composable
fun ProfileContent() {

    Column(
        modifier = Modifier
            .fillMaxWidth()
            .padding(24.dp),
        horizontalAlignment = Alignment.CenterHorizontally
    ) {

        // Foto Profil
        Image(
            painter = painterResource(
                id = R.drawable.fotoprofil
            ),
            contentDescription = "Foto Profil",
            contentScale = ContentScale.Crop,
            modifier = Modifier
                .size(120.dp)
                .clip(CircleShape)
                .background(Color.LightGray)
        )

        Spacer(modifier = Modifier.height(16.dp))

        Text(
            text = "Achmad Raffi Darmawan",
            fontSize = 24.sp,
            fontWeight = FontWeight.ExtraBold,
            color = DarkBlueText
        )

        Spacer(modifier = Modifier.height(6.dp))

        Text(
            text = "Mahasiswa",
            fontSize = 16.sp,
            color = TextGray
        )

        Spacer(modifier = Modifier.height(24.dp))

        // Informasi utama
        InfoItem(
            icon = Icons.Default.Person,
            label = "Nama",
            value = "Achmad Raffi Darmawan"
        )

        InfoItem(
            icon = Icons.Default.School,
            label = "NRP",
            value = "5053251047"
        )

        InfoItem(
            icon = Icons.AutoMirrored.Filled.MenuBook,
            label = "Program Studi",
            value = "Rekayasa Perangkat Lunak"
        )

        InfoItem(
            icon = Icons.Default.Email,
            label = "Email",
            value = "raffidarma2@gmail.com"
        )

        Spacer(modifier = Modifier.height(20.dp))

        HorizontalDivider(
            color = DividerColor,
            thickness = 1.dp
        )

        Spacer(modifier = Modifier.height(20.dp))

        // Informasi tambahan
        Text(
            text = "Informasi Tambahan",
            fontSize = 18.sp,
            fontWeight = FontWeight.Bold,
            color = DarkBlueText
        )

        Spacer(modifier = Modifier.height(16.dp))

        Row(
            modifier = Modifier.fillMaxWidth(),
            horizontalArrangement = Arrangement.spacedBy(12.dp)
        ) {

            AdditionalInfo(
                icon = Icons.Default.CalendarMonth,
                title = "Angkatan",
                value = "2025",
                modifier = Modifier.weight(1f)
            )

            AdditionalInfo(
                icon = Icons.Default.Place,
                title = "Domisili",
                value = "Surabaya",
                modifier = Modifier.weight(1f)
            )
        }

        Spacer(modifier = Modifier.height(20.dp))

        HorizontalDivider(
            color = DividerColor,
            thickness = 1.dp
        )

        Spacer(modifier = Modifier.height(16.dp))

        // Status
        Row(
            modifier = Modifier.fillMaxWidth(),
            horizontalArrangement = Arrangement.SpaceEvenly,
            verticalAlignment = Alignment.CenterVertically
        ) {

            StatusItem(
                icon = Icons.Default.Groups,
                text = "Mahasiswa Aktif"
            )

            VerticalDivider(
                modifier = Modifier.height(28.dp),
                color = DividerColor,
                thickness = 1.dp
            )

            StatusItem(
                icon = Icons.Default.School,
                text = "RPL"
            )
        }
    }
}

@Composable
fun InfoItem(
icon: ImageVector,
label: String,
value: String
) {

    Row(
        modifier = Modifier
            .fillMaxWidth()
            .padding(vertical = 8.dp),
        verticalAlignment = Alignment.CenterVertically
    ) {

        Box(
            modifier = Modifier
                .size(44.dp)
                .clip(RoundedCornerShape(12.dp))
                .background(IconBgColor),
            contentAlignment = Alignment.Center
        ) {

            androidx.compose.material3.Icon(
                imageVector = icon,
                contentDescription = label,
                tint = PrimaryBlue,
                modifier = Modifier.size(24.dp)
            )
        }

        Spacer(modifier = Modifier.width(14.dp))

        Column(
            modifier = Modifier.weight(1f)
        ) {

            Text(
                text = label,
                fontSize = 14.sp,
                color = TextGray
            )

            Text(
                text = value,
                fontSize = 17.sp,
                fontWeight = FontWeight.Bold,
                color = DarkBlueText
            )
        }
    }
}

@Composable
fun AdditionalInfo(
icon: ImageVector,
title: String,
value: String,
modifier: Modifier = Modifier
) {

    Card(
        modifier = modifier,
        shape = RoundedCornerShape(16.dp),
        colors = CardDefaults.cardColors(
            containerColor = IconBgColor
        )
    ) {

        Column(
            modifier = Modifier
                .fillMaxWidth()
                .padding(16.dp),
            horizontalAlignment = Alignment.CenterHorizontally
        ) {

            androidx.compose.material3.Icon(
                imageVector = icon,
                contentDescription = title,
                tint = PrimaryBlue,
                modifier = Modifier.size(26.dp)
            )

            Spacer(modifier = Modifier.height(8.dp))

            Text(
                text = title,
                fontSize = 13.sp,
                color = TextGray
            )

            Text(
                text = value,
                fontSize = 16.sp,
                fontWeight = FontWeight.Bold,
                color = DarkBlueText
            )
        }
    }
}

@Composable
fun StatusItem(
icon: ImageVector,
text: String
) {

    Row(
        verticalAlignment = Alignment.CenterVertically
    ) {

        androidx.compose.material3.Icon(
            imageVector = icon,
            contentDescription = text,
            tint = PrimaryBlue,
            modifier = Modifier.size(22.dp)
        )

        Spacer(modifier = Modifier.width(8.dp))

        Text(
            text = text,
            fontSize = 14.sp,
            fontWeight = FontWeight.Bold,
            color = DarkBlueText
        )
    }
}
```